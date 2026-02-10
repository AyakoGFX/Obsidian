bounce effects
```
amp = .04;
freq = 1.8;
decay = 3;
n = 0;
time_max = 3;

if (numKeys > 0) {
    n = nearestKey(time).index;
    if (key(n).time > time) {
        n--;
    }
}

if (n == 0) {
    t = 0;
} else {
    t = time - key(n).time;
}

if (n > 0 && t < time_max) {
    v = velocityAtTime(key(n).time - thisComp.frameDuration / 10);
    
    // Ease Out Factor (starts at 1, gradually reduces to 0)
    easeFactor = easeOut(t, 0, time_max, 1, 0);
    
    value + v * amp * Math.sin(freq * t * 2 * Math.PI) / Math.exp(decay * t) * easeFactor;
} else {
    value;
}
```

```
amp = .04;
freq = 1.8;
decay = 3;
n = 0;
time_max = 3;

if (numKeys > 0) {
    n = nearestKey(time).index;
    if (key(n).time > time) {
        n--;
    }
}

if (n == 0) {
    t = 0;
} else {
    t = time - key(n).time;
}

if (n > 0 && t < time_max) {
    v = velocityAtTime(key(n).time - thisComp.frameDuration / 10);
    
    // Ease Out Factor (starts at 1, gradually reduces to 0)
    easeFactor = easeOut(t, 0, time_max, 1, 0);
    
    value + v * amp * Math.sin(freq * t * 2 * Math.PI) / Math.exp(decay * t) * easeFactor;
} else {
    value;
}
```

```
freq = 3;
decay = 6;
n = 0;

if (numKeys > 0) {
  n = nearestKey(time).index;
  if (key(n).time > time) {
    n--;
  }
}

t = (n > 0) ? time - key(n).time : 0;

if (n > 0) {
  amp = velocityAtTime(key(n).time - 0.001);
  w = freq * Math.PI * 2;
  wave = Math.sin(t * w) / Math.exp(decay * t) / w;
  value + amp * wave;
} else {
  value;
}

```