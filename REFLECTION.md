# REFLECTION

## Effect each of the P, I, D components had in implementation
The P component is the one with the most visible effect on the car's behavior. As the P component has a direct connection with the amount of error the current trajectory is producing, it has the effect of determining how sharp the car can turn to adjust it's position in regards to the ideal position. The higher the P component is, the sharper the car can turn, but with the negative effect of overshooting the desired trajectory. Inversely, the lower the P component is, the longer it takes for the car to make a turn, which may be fatal on sharp turns, but with the positive effect of less overshoots. One should tune the P component to balance this two effects.

The I component has a role in dealing with the internal bias of the car steering. In practice, tuning the I component doesn't really show big difference in the car's behavior.

The D component is as important as the P component, and also shows visible effect on the car's behavior. It has a role of dealing with overshooting trajectory caused by the P component. In practice, this means keeping the car as close to the ideal trajectory as possible at all time, minimizing overshoots and oscillations. This however can cause a problem in some situation such as a big turn, where the D component will force the car to turn back to the middle of the road mid turn, which can cause the car to go all the way to the side of the road because the road is still turning. One then should tune the D component to balance this 2 effects.

## How the final hyperparameters were chosen
I started with the parameters found in the class quiz, which is 3.275, 0.0327, and 9.3 for P, I, D respectively. I then proceed to tune those parameters manually using educated guesswork.

First I tune the P parameter, and found that increasing it resulted in the car overshoots too much. Then I decrease it iteratively until the car can pass several turns. But tuning only the P param doesn't make the car pass the whole circuit.

I then turn to D parameter for tuning. Increasing it resulted in the car become more centered on the road, so I decided to increase it iteratively. Increasing the D param while at the same time decreasing the P param resulted in the car successfully passing the whole circuit.

Then I turn to I param to see how it affects the car's behavior. Tuning it's value doesn't seem to change much of the car's behavior, so I decided to keep it at a small value.

Finally, I tried to make the car run with higher velocity, so I increase the throttle value iteratively. Tuning the P, D, and throttle value furthermore resulted in the final parameter values as below.

P | I | D | Throttle
--- | --- | --- | ---
0.2 | 0.005 | 100 | 0.65
