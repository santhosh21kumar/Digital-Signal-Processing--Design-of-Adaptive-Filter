# Digital-Signal-Processing--Design-of-Adaptive-Filter

## AIM:
To Design and Implementation of Adaptive filters using MATLAB.

## SOFTWARE REQUIRED:
MAT LAB R2012

## ALGORITHM:
Step 1: Open mat lab. Write the program.

Step 2: Generating the desired signal. 

Step 3: Generating a signal corrupted with noise

Step 4: Estimating the signal. 

Step 5: Computing the Error signal. 

Step 6: Plot all the signals with x-label and y-label with suitable title

Step 7: Terminate the program.

## PROGRAM: 

```
clc;
clear all;
close all;
%Generating the desired signal
t=0.001:0.001:1
D=2*sin(2*pi*50*t);
%Generating a signal corrupted with noise
n=numel(D);
A=D(1, n) +0.9*randn(1, n);
l=D-A;
rr=[];
k=1;
r=xcorr(A);
M=25;
for i=1:1:M
rr(i) =r(n-i+1);
end
R=toeplitz(rr);
I=inv(R);
p=xcorr(D,A);
for i=1:1:M
P(i) =p(n-i+1);
end
w=inv(R') *P';
k=1;
%Estimating the signal
Est=zeros(n, 1);
for i=M:n
j=A(i:-1:i-M+1);
Est(i) =(w)'*(j)';
end
%Computing the Error signal
Err=Est'-D;
%Display of signal
subplot (4,1,1), plot(D)
title('Desired Signal');
subplot (4,1,2), plot(A)
title('Signal corrupted with noise');
subplot (4,1,3), plot(Est)
title('Estimated Signal');
subplot (4,1,4), plot(Err)
title('Error Signal');
```

## OUTPUT:
<img width="953" height="710" alt="Screenshot 2025-11-21 132253" src="https://github.com/user-attachments/assets/da974afd-e577-4891-a883-5c4199b774bf" />

## RESULT:
![WhatsApp Image 2025-11-28 at 22 37 50_3e6d1a7a](https://github.com/user-attachments/assets/e149b5bc-d54b-4525-9c68-cc93a069611e)

