
## Sensor setup and calling agent step.

1. Look at AgentWrapper to setup sensors and register handlers.
2. Ater tick, instead of run_step, call the agent (__call__), which does not take any input. The sensors need some time to read data from server. So, the data provider waits. We don't have to do anything as this is handled by the call method.


## Route planning:
1. We need to set the __global_plan of the agent. It can be done the way BasicAgent finds a route:

```
self._plan = self._agent.trace_route(
    self._map.get_waypoint(CarlaDataProvider.get_location(self._actor)),
    self._map.get_waypoint(self._target_location))
self._agent.set_global_plan(self._plan)
```