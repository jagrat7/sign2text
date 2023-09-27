# Sign2Text
Provide individuals who primarily rely on American Sign Language (ASL) to communicate remotely with an audience who do not understand ASL. The app translates ASL signs shown to camera to English in real-time, broadcasts the
translation to one or multiple audience through a virtual room.

## MVPs
- User must be able to access the cloud hosted application from any web browser.
- Any user must be able to create or join a room. (restricted to 1 room for MVP)
- User must be able to join room either as ASL or non ASL user by entering name.
- Provide a mechanism for ASL user to capture hand gestures through a camera and click photos to be
translated.
- The translated text generated from photos must be displayed on the Non-ASL/ASL end with low
latency.
- Application is restricted to ASL characters for MVP. Communication was restricted to one way for
MVP.
### Enhancements Done
- Bidirectional Communication: All users (both ASL and non ASL) in the same room can communicate simultaneously and remotely.
- Creation and isolation of users by multiple chat rooms.

## Architecture Diagram
![Architecture Diagram](/docs/arch_diagram.png)

Amplify: used to deploy the front-end React application.
EC2: used to host the Message transformation service, Chatroom Service, and ML service.
Kafka: used to route and store messages between the different services. Also used to manage rooms (topics).
Sage Maker Notebooks: Experiment and Train AWS models
Sage Maker inference: Provide predictions through a REST endpoint.
S3: used to store training data and models.
DynamoDB: used to store details of chat rooms and Kafka topics.
Application Load Balancer: used to route requests among multiple ECS containers running Chatroom Service.
CloudWatch: used to monitor various applications and services.
ECS: used to host and manage the deployment of Chatroom Service containers.

#### Note
This infrastructure was set up and deployed using terraform.

## Image Recognition
![Image Recognition](/docs/img_rec.png)
