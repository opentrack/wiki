**Please don't use 2.2 anymore. If 2.3 doesn't work for you, report what's wrong on the issue tracker so we can fix it. Also, this text uses too much passive voice and is harder to understand than necessary.**

The page describes how to achieve proper results using the Accela
filter, i.e.  prevent game output from jumping all over, while still not
having perceivable movement latency.

Separate smoothing values for rotation and translation are used. Higher
the value, more filtering is performed, causing latency.

Lower the second and third-order settings, larger the influence of
frame_(-1) and frame_(-2) on the tracker output. With reasonably low
values, the higher amount of change across all last 3 frames, less lag
the filter causes.

Deadband's a minimal change to influence the tracker. By setting the
value in fractions of a degree, noise gets removed before it begins to
become smoothed. This results in lesser smoothing required at a
negligible cost in accuracy.

Finally, exponent's the gain of the filter, i.e. higher exponent causes
slower response to minimal input, with a more immediate response to
major output. Keep in mind that larger exponents cause the delay to pile
up, resulting in a spike after passing a threshold value.

Whether settings are close to optimal depends on the tracker used,
particular sensor, but also on the mapping. As filtering's done
before mapping gets applied, conservative mappings need less
filtering to be effective.
