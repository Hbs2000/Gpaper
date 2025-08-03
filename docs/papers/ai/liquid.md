# Liquid Time-Constant Networks

传统连续时间的 RNN 的隐藏状态由 ODE 描述

$$
\begin{equation}
\frac{dx(t)}{dt}=f(x(t),I(t),t,\theta)
\end{equation}
$$

$f$ 是由神经网络参数化的函数，$x(t)$ 是隐藏状态，$I(t)$ 是输入信号，一般是通过数值 ODE solver 求解（如 Runge-Kutta），并利用伴随方法（Adjoint Method）反向传播梯度。

但是固定的动态方程，难以建模复杂多时间尺度的信号，并且直接使用神经网络定义动态可能导致梯度爆炸 / 消失。

传统动力学模型 (Funahashi-Nakamura, 1993) 提出

$$
\begin{equation}
\frac{dx(t)}{dt}=-\frac{x(t)}{\tau}+f(x(t),I(t),t,\theta)
\end{equation}
$$

其中，$\tau$ 是预设的静态参数，无法根据输入动态调整，并且所有的隐藏状态单元共享相同的动态模式（如响应速度），缺乏灵活性。

Liquid Time Constant model 则将隐藏状态的动态分解为线性 ODE 和非线性门控的耦合，其中系统的时间常数从固定值 $\tau$ 变为动态调整值。

$$
\begin{equation}
\tau_\mathrm{sys}=\frac{\tau}{1+\tau f(x(t),I(t),t,\theta)}
\end{equation}
$$

$$
\begin{equation}
\tau_i/(1+\tau_iW_i)\leq\tau_{sys_i}\leq\tau_i,
\end{equation}
$$













