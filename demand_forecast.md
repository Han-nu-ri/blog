(a) Simple exponential smoothing,
$$
y_t=\alpha D_{t-1}+({1-\alpha}) y_{t-1}.
$$
with alpha=0.3.
$$
y_2=0.3D_1+0.7y_1=D_1=1000 \\
y_3=0.3D_2+0.7y_2=(0.3)*1113+0.7*1000 \\
\vdots \\
y_{12}=0.3D_{11}+0.7y_{11}\\
y_{13}=0.3D_{12}+0.7y_{12}\\
$$ 

(b) Double exponential smoothing,
$$
y_t=I_{t-1}+S_{t-1} \\
= \alpha D_{t-1}+(1-\alpha)(I_{t-2}+S_{t-2}) \\
= \beta (I_{t-1}-I_{t-2}
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzEwODUzODc2LDkxNjcyNjQ1OCwtMTEyNz
kwMzk3MiwzMTMyODA5OTcsNzMwOTk4MTE2XX0=
-->