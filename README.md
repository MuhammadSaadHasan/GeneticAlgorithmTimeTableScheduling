# Timetable Scheduling Genetic Algorithm

## Overview

This project addresses the university timetable scheduling problem using a genetic algorithm. The goal is to create a timetable that minimizes clashes between sections, professors, and rooms, while satisfying various hard and soft constraints. The solution considers multiple factors such as room capacity, class types (theory and lab), professor assignments, and course schedules.

## Features

- Schedules theory and lab classes
- Ensures no clashes in room usage, professor assignments, and section schedules
- Considers room capacity for different class types
- Ensures lab sessions are in the afternoon and theory classes are in the morning
- Allows for soft constraints like minimizing movement between floors and continuous teaching blocks

## Project Structure

```plaintext
timetable/
├── data/
│   ├── data.xlsx
│   ├── timetable.xlsx
├── main.py
└── README.md
```

- `data/`: Contains the input data files.
  - `data.xlsx`: Contains course details such as code, name, credit hours, section, and instructor.
  - `timetable.xlsx`: Contains room details and capacities.
- `main.py`: The main script that implements the genetic algorithm for timetable scheduling.
- `README.md`: Documentation for the project.
- `requirements.txt`: List of Python dependencies required for the project.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/timetable-scheduling.git
   cd timetable-scheduling
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Place your input data files (`data.xlsx` and `timetable.xlsx`) in the `data/` directory.

2. Run the main script:
   ```bash
   python main.py
   ```

3. The script will process the data and generate a timetable using a genetic algorithm. The final timetable will be printed in the console.

## Configuration

### Input Data Format

#### data.xlsx
- Should contain sheets with the following columns:
  - `Code`: Course code
  - `Course`: Course name
  - `CHs`: Credit hours
  - `Section`: Section identifier
  - `Course Instructor`: Instructor name

#### timetable.xlsx
- Should contain room details with columns:
  - `Room`: Room name or identifier
  - `Type`: Room type (classroom or lab)
  - `Capacity`: Room capacity

### Time Slots

The time slots are defined within the script and include:
- Morning sessions: 08:30-09:50, 10:00-11:20, 11:30-12:50, 01:00-02:20, 02:30-03:50
- Afternoon sessions: 03:55-05:15, 05:20-06:40, 06:45-08:05

### Constraints

#### Hard Constraints
- Classes can only be scheduled in free classrooms.
- Room capacity must be sufficient for the section size.
- No professor should be assigned to multiple lectures simultaneously.
- No section should be scheduled in multiple rooms simultaneously.
- No room should be assigned to multiple sections simultaneously.
- Professors can teach a maximum of 3 courses.
- Sections can have a maximum of 5 courses.
- Courses should have two lectures per week on non-adjacent days.
- Lab lectures must be conducted in two consecutive slots.
- A 15-minute break is allowed between consecutive classes.

#### Soft Constraints
- Theory classes in the morning, lab sessions in the afternoon.
- Minimize movement between floors for teachers and students.
- Consistent classroom assignment throughout the week.
- Minimize interruptions by preferring longer teaching blocks.

## Genetic Algorithm Implementation

1. **Initialization**: Generate an initial population of possible timetables.
2. **Fitness Calculation**: Evaluate the fitness of each timetable based on the constraints.
3. **Selection**: Select the best-performing timetables for reproduction.
4. **Crossover**: Combine parts of two parent timetables to create offspring.
5. **Mutation**: Introduce random changes to some offspring to maintain diversity.
6. **Iteration**: Repeat the selection, crossover, and mutation steps for a number of generations.
7. **Result**: The timetable with the highest fitness score after all generations is considered the best solution.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

This project is inspired by classical university timetabling problems and leverages genetic algorithms to provide a feasible solution.
