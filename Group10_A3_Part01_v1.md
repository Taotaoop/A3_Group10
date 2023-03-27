# UofM Computer Science Crouse API

## API description
This API is designed to support enrollment at UofM. This set of APIs would provide a list of information related to the courses they are interested in. Students could specify relevant parameters to retrieve crouse information.

## Endpoints and Parameters
#### Endpoint
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}&{CourseName}```
#### Patameters
| Parameter  | Type   | Description  | Required  |
|------------|--------|--------------|-----------|
| Year       | Int    | the academic year in which the course is being offered. Ex:2023|  Yes |
| Term       | String | the specific part of the academic year. Ex:Fall, Winter        |  No  |
| CourseName | String | the name of the specific course. Ex:COMP3040                   |  No  |

## Description of Resources
It will get bunch of information of one course or a list of courses.  
```
CourseName(String)  
The course number and the course name.
```
```
Prerequisites(String)  
The prerequisites of the course.
```
```
Description(String)
The description of the course.
```
```
Credits(int)
How many credits of the course.
```
```
Section(JSON Object)
The specific information for each lecture section.
There is an array for each lecture section.
First value in array is instruction's name(String), 
second value is days of lectures(String), 
third value is the time of each lecture(String),
fourth value is the course duration(String),
fifth value is the course capacity(int).
```
```
Lab(JSON Object)
The specific information for each lab section.
There is an array for each lab section.
First value in array is TA's name(String), 
second value is days of labs(String), 
third value is the time of each lab(String),
fourth value is the course duration(String),
fifth value is the lab capacity(int).
```
```
Attribute(String)
The attribute of the course.
```
 Response Example
```json
{
  "CourseName": "COMP 3430 Operating Systems",
  "Prerequisites": "one of COMP 2140 or COMP 2061; and COMP 2280 or ECE 3610.",
  "Description": "Operating systems, their design, implementation, and usage.",
  "Credits": 3,
  "Section": {
    "A01": ["Franklin Bristow", "MWF", "8:30am-9:20am", "01/09-04/12", 90],
    "A02": ["Robert W. Guderian", "TR", "10:00am-11:15am", "01/09-04/12", 90]
  },
  "Lab": {
    "B01": ["Justin Smith", "T", "04:00 pm-05:15 pm", "01/09-04/12", 25],
    "B02": ["Kathie Anderson", "R", "04:00 pm-05:15 pm", "01/09-04/12", 25]
  },
  "Attribute": "Science Requirement for BA, Science"
}
```

## Sample Request with Sample Response
