Aruco is an paper marker tracker.

To use it, execute the "clientfiles/aruco/aruco\_create\_marker.exe"
utility, or print the sample [AR marker image](https://github.com/opentrack/opentrack/blob/47c15a2aa82192033882c06b58a478525683df4a/facetracknoir/clientfiles/aruco/test3.jpg).

Following that, base it on cardboard, avoiding either glue bleeding
through the paper, or tape covering the marker respectively, depending
on the method used. Leave two or three centimerers of the empty paper around
the markings.

Please keep in mind that marker has to be waved at the camera at a
neutral pitch angle of at least 15-25 degrees -- since it's planar,
solver gets confused when pose approaches identity. When
mounting it on a hat, ensure a relatively oblique angle that
keeps the raw pitch value positive at all times. Otherwise,
sudden spikes in pitch value ensue.
