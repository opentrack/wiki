# UDP Protocol

The **UDP over network** protocol in opentrack allows external applications to send or receive head-tracking data over a UDP connection. This is useful for custom clients, game integrations, or third-party applications that consume opentrack's output. It can also be used to get data from external sources (Phone-based trackers, other machines, etc...).

## Protocol Specification

The protocol uses 48-byte UDP packets containing 6 IEEE 754 double-precision floating-point values (8 bytes each), sent in little-endian byte order.

### Packet Structure

| Offset (bytes) | Field | Type   | Unit        | Description                          |
|---------------:|-------|--------|-------------|--------------------------------------|
| 0–7            | x     | double | centimeters | Translation along the X axis         |
| 8–15           | y     | double | centimeters | Translation along the Y axis         |
| 16–23          | z     | double | centimeters | Translation along the Z axis         |
| 24–31          | yaw   | double | degrees     | Rotation around the vertical axis    |
| 32–39          | pitch | double | degrees     | Rotation around the lateral axis     |
| 40–47          | roll  | double | degrees     | Rotation around the longitudinal axis|

## Configuration

In opentrack, select UDP over network as the output method and configure the desired UDP host and port. Make sure the port is open in your firewall.

## Code Examples

The following examples are recievers that you can adapt to your use case.

### Python

A minimal Python client that receives tracking data via UDP:

```py
import socket
import struct

UDP_IP = "0.0.0.0"  # Listen on all available interfaces
UDP_PORT = 4242    # Port number

# Create a UDP socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind((UDP_IP, UDP_PORT))

print(f"Listening for UDP packets on {UDP_IP}:{UDP_PORT}")

try:
    while True:
        data, addr = sock.recvfrom(48)
        out = ""
        for (i, label) in enumerate(["x:", "y:", "z:", "Yaw:", "Pitch", "Roll"]):
            dp: float = struct.unpack('d', data[i*8:(i+1)*8])[0]
            out += f"{label} {round(dp, 2)}\t"
        print(f"From {addr}: {out}")
except Exception:
    sock.close()
```

### C#

A minimal C# receiver for opentrack UDP output:

```csharp
using System;
using System.Net;
using System.Net.Sockets;

class UDPReceiver
{
    static void Main()
    {
        string localAddress = "0.0.0.0";
        int localPort = 4242;

        using var udpClient = new UdpClient(new IPEndPoint(IPAddress.Parse(localAddress), localPort));
        var remoteEndpoint = new IPEndPoint(IPAddress.Any, 0);

        Console.WriteLine($"Listening for UDP packets on {localAddress}:{localPort}");

        while (true)
        {
            if (udpClient.Available < 48)
                continue;

            // Drain all available data and keep only the latest packet
            byte[] data = null;
            while (udpClient.Available >= 48)
                data = udpClient.Receive(ref remoteEndpoint);

            if (data == null || data.Length < 48)
                continue;

            double x = BitConverter.ToDouble(data, 0);
            double y = BitConverter.ToDouble(data, 8);
            double z = BitConverter.ToDouble(data, 16);
            double yaw = BitConverter.ToDouble(data, 24);
            double pitch = BitConverter.ToDouble(data, 32);
            double roll = BitConverter.ToDouble(data, 40);

            Console.WriteLine($"x: {x:F2}, y: {y:F2}, z: {z:F2}, " +
                              $"yaw: {yaw:F2}, pitch: {pitch:F2}, roll: {roll:F2}");
        }
    }
}
```
