# Exercise-rep-counter
An AI-powered web application built with Python, Flask, OpenCV, and Google MediaPipe. The system uses computer vision and pose estimation to track human movement in real-time, calculating elbow joint angles to provide live form correction and accurate rep counting for bicep curls.

🧠 How the AI Logic Works
Landmark Extraction: The application captures live frames from your webcam and tracks the exact 3D spatial coordinates $(x, y, z)$ of your Right Shoulder, Right Elbow, and Right Wrist.
Angle Calculation: Using inverse trigonometric functions (np.arctan2), the code calculates the exact changing angle of the elbow joint.
State Machine Processing:
      Elbow Angle > 160°: The arm is registered as completely straight. The application marks the phase state as down and prompts the user to pull up.
      Elbow Angle < 30°: The bicep is fully contracted. If the user was previously in the down state, a complete repetition is validated, the counter increments by $1$, and the state changes to up.
      Cheat Prevention: If a user performs a partial rep (failing to go below 160° or above 30°), the state machine will not trigger, and the movement won't be counted as a repetition.
