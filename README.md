# Training Scheduler

A console application to help schedule different sessions that will be available on a training day, distributing the sessions over multiple days (if required) thus giving every session an unbiased opportunity to be presented

### Prerequisites

* Visual Studio 2019
* Enable NuGet Package Restore

```
Allow NuGet to download missing packages
Automatically check for missing packages during build in Visual Studio
```

### Installing and Running the application

Do git clone and build the solution locally. 
To change the input data, edit file - *session_info.json*.
Run the application and view the output on console.

### Running the tests

**TrainingSessionManagement.Test** is the test case project for the application

## Business Logic

The program runs till all sessions are consumed. 
*Morning sessions* is of 180 minutes. If no exact combination of sessions found, then the combination closest to 180 minutes is choosen. 

*Aternoon sessions* duration range from 180-240 minutes. Right after afternoon session, the *sharing session* starts.
If the *afternoon session* ends before 4:00pm, then the *sharing session* starts at 4:00pm.

The sessions with duration more than 240 minutes, gets a new track.

### Core logic

* Sessions are first allocated for morning slot followed by afternoon slot
* For morning slot, sessions are picked at random untill they add-up to 180 mins
* If the set of randomly picked sessions donot addup to 180, the program back tracks to check for alternatives keeping a lookup set of already traversed path so that re-computation can be prevented
* If exact sum i.e. 180 mins is not found, then the program chooses the closest possible match
* Similar computation applies for afternoon slot

## Authors

**K Rajesh Kumar**

