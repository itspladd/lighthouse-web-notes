# REST Exercise

You are asked to build an API for a photo app.
You need to create the routes according to REST for the following actions:

1. The end-user wants to see a list of photos: `GET '/photos'`

2. The end-user wants to see a particular photo: `GET '/photos/:photoid'`

3. The end-user wants to upload a new photo: 
* `GET '/photos/new'`
* `POST '/photos'`

4. The end-user wants to update an existing photo: 
* `GET '/photos/:photoid'`
* `PUT '/photos/:photoid'`

5. The end-user wants to see a list of user profiles: `GET '/users'`

6. The end-user wants to see a specific profile: `GET '/users/:userid'`

7. The end-user wants to see a list of the photos for a specific profile: `GET '/users/:userid/photos'`

8. The end-user wants to see one particular photo of a particular user: `GET '/users/:userid/photos/:photoid'`