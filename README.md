# Baseball-Pitch-Simulation
Baseball pitch simulation created on Matlab using a Simulink block model. Livescript containing analysis of three MLB pitchers using the block model to simulate pitch arsenals and conduct pitch analysis. Repository contains two block models: Baseball_Sim2 and Baseball_Sim3. Sim3 contains release points x and y, while Sim2 only contains release point y or release height. Both block models are needed to run the livescript containing pitch analysis. Simulink Block Model has inputs: release points (x and y), spin angle, spin rate, and release velocity. 

## To use block model: 
Before running simulation, set relative/absolute tolerance and step size to ensure accurate results:
```
set_param("Baseball_Sim2", "MaxStep", "0.0001");
set_param("Baseball_Sim2", "RelTol",  "1e-5");
set_param("Baseball_Sim2", "AbsTol",  "1e-8");
```
It is effective to initialize all inputs to the block model as Simulink Parameters: <br/>
```
input_name = Simulink.Parameter(value)
```
Parameter values can be changed:
```
input_name.Value = new_Value
```
After initializing all inputs as Simulink Parameters, run simulation/store results, and plot. Set axes. <br/>
```
pitcher_pitch = sim("Baseball_SimX.slx")
plot3(pitcher_pitch.x, pitcher_pitch.z, pitcher_pitch.y)
axis([0 19 -1 1 0 2]);
```
As a frame of reference for each pitch, the user should also simulate the pitch without spin in order to calculate break/induced movement. Function in the livescript plotStrikeZone can be used to put a strikezone in your pitch trajectory plot:
```
hold on; plotStrikeZone; hold off;
```
