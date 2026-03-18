# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 
```
clc;
clear;
close;

disp("🎤 Loading audio files...");

// Read reference and test voice files
[y1, fs1] = wavread("C:\Users\acer\Downloads\referance.wav");
[y2, fs2] = wavread("C:\Users\acer\Downloads\test.wav");

// Check sampling rates
if fs1 <> fs2 then
    error("❌ Sampling rates must match!");
end

// Convert stereo to mono (if needed)
if size(y1,2) == 2 then
    y1 = mean(y1, 2);
end
if size(y2,2) == 2 then
    y2 = mean(y2, 2);
end

// Make both signals same length
n = min(length(y1), length(y2));
y1 = y1(1:n);
y2 = y2(1:n);

// Compute Euclidean distance
dist = sqrt(sum((y1 - y2).^2));

disp("Euclidean distance (reference vs test): " + string(dist));

// Decision based on threshold
if dist < 0.5 then
    disp("✅ Matching with reference (same word)");
else
    disp("❌ Not matching with reference (different word)");
end

// Plot both signals
figure(0);
subplot(2,1,1);
plot(y1);
title("REFERENCE VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

subplot(2,1,2);
plot(y2);
title("TEST VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

// Comparison plot
figure(1);
plot(y1, 'b');
plot(y2, 'r');
title("Reference (Blue) vs Test (Red) Signal");
xlabel("Samples");
ylabel("Amplitude");
legend(["Reference", "Test"]);

disp("✅ Waveforms plotted successfully.");
```

## OUTPUT: 
<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/8601c689-8318-4d0b-aa62-1b337ae5756f" />

<img width="1918" height="1198" alt="image" src="https://github.com/user-attachments/assets/9dc4fd6e-085f-4b24-b570-391287de71c7" />

## RESULT: 
Thus the speech recognition using SCILAB was performed and verified.
