<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: SANJAY K</h3>
<h3>Register Number: 212223220094</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>The Firefighting Drone Agent</strong></td>
    <td><strong>The agent’s performance depends on maximizing fires extinguished while minimizing random moves.</strong></td>
     <td><strong>Cities,Forest,Mountains Regions</strong></td>
    <td><strong>Putoff the Fire</strong></td>
    <td><strong>Location, Temperature of Environment</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
<h3>PROGRAM:</h3>

    import random
    class ForestEnvironment:
       def __init__(self, size=4, fire_count=2):
        self.size = size
        self.grid = [["Tree" for _ in range(size)] for _ in range(size)]
        for _ in range(fire_count):
            x, y = random.randint(0, size-1), random.randint(0, size-1)
            self.grid[y][x] = "Fire"
        self.drone_position = [0, 0]

    def get_cell_status(self):
        x, y = self.drone_position
        return self.grid[y][x]

    def extinguish_fire(self):
        x, y = self.drone_position
        if self.grid[y][x] == "Fire":
            self.grid[y][x] = "Tree"
            return True
        return False

    class FirefightingDrone:
    def __init__(self):
        self.score = 0

    def perceive_and_act(self, environment):
        state = environment.get_cell_status()
        if state == "Fire":
            environment.extinguish_fire()
            self.score += 30
            return f"Drone at {environment.drone_position}: Fire -> Extinguished"
        else:
            move = random.choice(["North", "South", "East", "West"])
            x, y = environment.drone_position
            if move == "North" and y > 0:
                environment.drone_position[1] -= 1
            elif move == "South" and y < environment.size-1:
                environment.drone_position[1] += 1
            elif move == "East" and x < environment.size-1:
                environment.drone_position[0] += 1
            elif move == "West" and x > 0:
                environment.drone_position[0] -= 1
            self.score -= 1
            return f"Drone moved {move} to {environment.drone_position}"

     def run_firefighting_simulation(steps=8):
    env = ForestEnvironment()
    agent = FirefightingDrone()

    for step in range(steps):
        print(agent.perceive_and_act(env))

    print("\nFinal Forest State:")
    for row in env.grid:
        print(row)
    print("Performance Score:", agent.score)

     run_firefighting_simulation(steps=8)

<h3>OUTPUT:</h3>
<img width="295" height="248" alt="Screenshot 2025-09-09 132431" src="https://github.com/user-attachments/assets/68f760e1-cf82-4a77-a607-b0a618b0c657" />

<h3>RESULT:</h3>
<p>Thus the above given program is executed successfully.</p>

