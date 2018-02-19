# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

---

## Model
> The model is a simplified version of how cars behave, it ignores tire forces, lateral forces, gravity and mass. Although such simplifications in kinematic models limit their use in a real world application, they are useful to develop control methods such as an MPC. It is important to mention that at low and moderate speeds, the kinematic models offer a good approximation of the real vehicle dynamics.

### Vehicle State
>The coordinates of the car provided by the simulator are in global coordinates. I transformed the coordinates with respect to the car and not the map.
>The state of the vehicle is described by
* x - Vehicle position in forward direction.
* y - Vechicle position in lateral direction.
* v - Vehicle's speed.
* psi - angle of vehicle (yaw).

### Actuators
> The actuators state describes how the orientation and velocity of our vehicle will change in time.
>The actuators are:
* delta - Steering angle (rad)
* a - acceleration

### Update Step
>The update step is used to compute the next state of the car, regarding the current state. 
>I used a third degree Polynomial to compute the trajectory of the car. I tried a higher degree polynomial but it was leading to overfitting.

>I first found that 6 timesteps at a frequency of 15 worked good for low speeds like 20 mph but when I started to increment the speed I found that a higher timestep helped. I ended with velocity set to 60 mph with 9 timesteps and dt = 0.2

### Latency
>First I tried with low latency and I was able to get the car going very fast. With the 100 millisecond latency I needed to slow the car down to 60 mph for a smoother ride but the MPC is capable to handle the high latency which simulates the kind of latency found in real life.
