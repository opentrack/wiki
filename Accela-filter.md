For the math buffs out there, Accela mk4 is a nonlinear 3rd-order finite impulse response filter with a deadband component.

The page describes how to achieve proper results using the filter, i.e. prevent game output to jump all over, while still not having perceivable movement latency.

Separate smoothing values for rotation and translation are used. Higher the value, more filtering is performed, causing latency.

Lower the second and third-order settings, larger the influence of frame-2 and frame-3 on the tracker output. With reasonably low values, a tendency to change a degree of freedom within all 3 frames to one side causes the tracker to respond faster. When this isn't the case, observation has been made that often the noise tends to cancel itself out throughout the 3 frames in the filter's history. On the other hand, setting a high value for second and third-order values negates their influence, causing only the last frame to decide the filtered position.

Deadband's a minimal change to influence the tracker. By setting the value in fractions of a degree, noise gets removed before it begins to become smoothed. This results in lesser smoothing required at a negligible cost in accuracy.

Finally, exponent's the gain of the filter, i.e. higher exponent causes slower response to minimal input, with a more immediate response to major output. Keep in mind that larger exponents cause the delay to pile up, resulting in a spike after passing a threshold value.

Whether settings are close to optimal depends on the tracker used, particular sensor, but also on the mapping. As filtering's done before mapping gets applied, conservative mappings need less filtering to be effective.