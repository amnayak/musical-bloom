Data structures:
- bool user_input_enabled; //true when listening for user input (use in keypress handler)
- Vector<int> user_vector; //stores user input, cleared after every round
- Vector<int> generated_vector; //stores generated sequence, initialized with one value
- string[4] cube = {"RedCube", "BlueCube", "GreenCube", "YellowCube"} //converts vector value to mesh
- string[4] cube_chime = {"RedChime", "BlueChime", "GreenChime", "YellowChime"} //converts vector value to chime
- bool[4] is_bloom = {false, false, false, false} //converts vector value to whether corresponding cube has bloom
- string failureChime;
- string successChime;

Constants:
- Amount of time a chime plays/ a bloom is active

Utils needed:
- timer for spacing out chimes played
- random int generator [0,3]

Game loop:
1) play chimes and bloom cubes in sequence (user_input off) from generated_vector (use is_bloom)
2) listen for user_input while user_vector.size < generated_vector.size
    - if user_vector != generated_vector[0 ... user_vector.length]
      - play "failure chime" and end game, print out score aka generated_vector.size - 1
    - update is_bloom
3) clear user_vector, add random value to generated_vector, play "success chime"

User input:
If user_input enabled, On WASD, append to user_vector and play cube_chime
