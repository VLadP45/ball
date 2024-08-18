# ballclass SoccerBall:
    def __init__(self):
        self.position = (0, 0)  # Ball starts at the origin
        self.is_in_motion = False

    def kick(self, direction, distance):
        if not self.is_in_motion:
            self.is_in_motion = True
            dx, dy = direction
            new_x = self.position[0] + dx * distance
            new_y = self.position[1] + dy * distance
            self.position = (new_x, new_y)
            print(f"Ball kicked to position {self.position}.")
        else:
            print("Ball is already in motion!")

    def stop(self):
        if self.is_in_motion:
            self.is_in_motion = False
            print("Ball stopped.")
        else:
            print("Ball is already stationary.")

    def pass_ball(self, direction, distance):
        if not self.is_in_motion:
            self.kick(direction, distance)
            print(f"Ball passed to new position {self.position}.")
        else:
            print("Cannot pass the ball while it's in motion.")

    def get_status(self):
        motion_status = "in motion" if self.is_in_motion else "stationary"
        print(f"Ball is currently {motion_status} at position {self.position}.")


# Example usage:
ball = SoccerBall()

ball.get_status()
ball.kick((1, 1), 10)  # Kick the ball 10 units in the (1, 1) direction
ball.get_status()
ball.stop()
ball.pass_ball((0, 1), 5)  # Pass the ball 5 units in the (0, 1) direction
ball.get_status()
