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
= \alpha D_{t-1}+(1-\alpha)(I_{t-2}+S_{t-2}) \\ + \beta (I_{t-1}-I_{t-2})+(1-\beta)S_{t-2}.
$$
with alpha=0.05, beta=0.1.
$$
y_1=I_
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA1MTYxNTk4MCw5MTY3MjY0NTgsLTExMj
c5MDM5NzIsMzEzMjgwOTk3LDczMDk5ODExNl19
-->