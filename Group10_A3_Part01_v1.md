# UofM Find Course API
This API is designed to support enrollment at UofM. This set of APIs would provide a list of information related to the courses they are interested in. Students could specify relevant parameters such as Year, Term and CourseID to retrieve course information.
## API description
Our API is a simple REST api, where user can do GET requests to the endpoint.

## Endpoints and Parameters
#### Endpoint
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}&{CourseID}```
#### Patameters
| Parameter  | Type   | Description  | Required  |
|------------|--------|--------------|-----------|
| Year       | Int    | the academic year in which the course is being offered. Ex:2023|  Yes |
| Term       | String | the specific part of the academic year. Ex:Fall, Winter        |  Optional  |
| CourseID   | String | the ID of a specific course. Ex:COMP3040                       |  Optional  |

## Description of Resources
| **Parameters**  | **Type**  | **Description** |
|---|---|---|
| CourseID  | String  |  The subject and crouse number of a course. |
| CourseName  | String  |  The course title. |
| Prerequisites | String  | The prerequisites of the course.  |
| Description  | String  |  The description of the course. |
| Credits | Int  | Credits hours of the course. |
| Section | JSON Object  |  The specific information for each lecture section. <br> <ul><li>Instruction's name (String)</li><li>Days scheduled (String)</li><li>Time scheduled (String)</li><li>Start and end dates for the course (String)</li> <li>Course Capacity (int)</li></ul> |
| Lab  | JSON Object  | The specific information for each lab section. <br> <ul><li>TA's name (String)</li><li>Days scheduled (String)</li><li>Time scheduled (String)</li><li>Start and end dates for the course (String)</li> <li>Lab Capacity (int)</li></ul> |
| Attribute  | String  | The attribute of the course  |


## Sample Requests
Here are the three sample requests for getting course information from our API:

### 1.List all Computer Science courses in a specific academic year.
```https://UofMCSEnrollment.ca/api/courses?{Year}```
#### Description
```{
     "result": [
     {
     "CourseID": "<String>" ,
     "CourseName": "<String>",
     "Credits"; "<Int>"
     },
     ...
```
####  GET Request
 ```
    https://UofMCSEnrollment.ca/api/courses?{2023}
  ```

#### Response
```json
  {
    "result":[
      {
        "CourseID": "COMP1010",
        "CourseName": "Introductory Computer Science 1",
        "Credits": 3,
      },
      {
        "CourseID": "COMP1012",
        "CourseName": "Computer Programming for Scientists and Engineers",
        "Credits": 3,
      },
      {
        "CourseID": "COMP1020",
        "CourseName": "Introductory Computer Science 2",
        "Credits": 3,
      },
      {
        "CourseID": "COMP2140",
        "CourseName": "Data Structures and Algorithms",
        "Credits": 3,
      },
      {
        "CourseID": "COMP2160",
        "CourseName": "Programming Practices",
        "Credits": 3,
      },
      {
        "CourseID": "COMP3020",
        "CourseName": "Human-Computer Interaction 1",
        "Credits": 3,
      }
    ]
  }
```
### 2. List all Computer Science courses in a specific academic year and term.
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}```
#### Description
```{
     "result": [
     {
     "CourseID": "<String>" ,
     "CourseName": "<String>",
     "Credits": "<Int>",
     "Section": "<Json Object>"
     },
     ...
```
 #### GET Request
```
https://UofMCSEnrollment.ca/api/courses?{2023}&{Winter}
```
  
#### Response
```json
  {     
    "result":[
      {
        "CourseID": "COMP1010",
        "CourseName": "Introductory Computer Science 1",
        "Credits": 3,
         "Section": {
          "A01": ["Franklin Bristow", "MWF", "8:30am-9:20am", "01/09-04/12", 90],
          "A02": ["Robert W. Guderian", "TR", "10:00am-11:15am", "01/09-04/12", 90]
        },
      },
      {
        "CourseID": "COMP1012",
        "CourseName": "Computer Programming for Scientists and Engineers",
        "Credits": 3,
        "Section": {
          "A01": ["Franklin Bristow", "TR", "10:30am-11:20am", "01/09-04/12", 90]
        },
      },
      {
        "CourseID": "COMP1020",
        "CourseName": "Introductory Computer Science 2",
        "Credits": 3,
         "Section": {
           "A01": ["Franklin Bristow", "MWF", "8:30am-9:20am", "01/09-04/12", 90],
           "A02": ["Robert W. Guderian", "TR", "10:00am-11:15am", "01/09-04/12", 90]
          },
      }
    ]
  }
 ```

### 3. List a specific Computer Science course in a specific academic year and term.
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}&{CourseID}```
#### Description
```
{
  "results":
  {
  "CourseID": "<String>",
  "CourseName": "<String>",
  "Prerequisites": "<String>",
  "Description": "<String>",
  "Credits": <Int>,
  "Section": {
    "<String>": ["<List>"],
    "<String>": ["<List>"]
  },
  "Lab": {
    "<String>": ["<List>"],
    "<String>": ["<List>"]
  },
  "Attribute": "<String>"
  }
}
```
 #### GET Request

  ```
  https://UofMCSEnrollment.ca/api/courses?{2023}&{Winter}&{COMP3430}
  ```

### Response 
```json
{
  "results":
  {
  "CourseID": "COMP3430",
  "CourseName": "Operating Systems",
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
}
```
