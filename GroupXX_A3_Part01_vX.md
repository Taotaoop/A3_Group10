# UofM Computer Science Crouse API

## API description
This API is designed to support enrollment at UofM. This set of APIs would provide a list of information related to the courses they are interested in. Students could specify relevant parameters to retrieve crouse information.

## Endpoints and Parameters
####Endpoint
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}&{CourseName}```
####Patameters
| Parameter  | Type   | Description  | Required  |
|------------|--------|--------------|-----------|
| Year       | Int    | the academic year in which the course is being offered. Ex:2023|  Yes |
| Term       | String | the specific part of the academic year. Ex:Fall, Winter        |  No  |
| CourseName | String | the name of the specific course. Ex:COMP3040                   |  No  |

## Description of Resources

## Sample Request with Sample Respons
