![image](https://user-images.githubusercontent.com/7758970/204094536-45b1bf58-ea32-42ca-9e63-fe9638886b9d.png)

## Endpoints

API Endpoint Host : http://103.134.154.18:30822/

I've deployed this project to my personal VPS, and deployed to `single-node kubernetes`

This project is configured to be able to containerized using docker (Dockerfile). <br> And deployed on a single-node kubernetes cluster. (Deployment.yaml)

Here is what i mean by single-node cluster, go checkout my story on medium here: <br>
https://reinhardjsilalahi.medium.com/beginners-guide-simple-hello-kubernetes-all-in-one-on-a-single-vps-fcfdfee9edfc


### Login
`POST` http://103.134.154.18:30822/login

Authentication : none

Example Body Payload:
```
{
    "email": "admin@email.com",
    "password": "password"
}
```

<br> 

Example Response Payload:
```
{
    "status": 200,
    "message": "this token will be valid for the next 3 minutes, login again if it expired",
    "data": {
        "email": "admin@email.com",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6ImFkbWluQGVtYWlsLmNvbSIsImV4cCI6MTY2OTQ3MjAxOH0.8KfQnlZHC8tFldiaqbj7DQlW7QwIbpWn16TBDSu_p9w"
    }
}
```

<br>

### Get position list
`GET` http://103.134.154.18:30822/positions?description={description}&location={location}&page={page}

Authentication : `Bearer <Token>`

<br>

### Get position
`GET` http://103.134.154.18:30822/positions/{position-id}

Authentication : `Bearer <Token>`

## Credentials
```
{
    "email": "admin@email.com",
    "password": "password"
}
```

<br>

Your token will be expiring for 3 minutes. You should request for new token from `/login` endpoint <br>
You can use non expiring token below, if u disturbed by the expired token

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VySWQiOiI2MzgwYzIxNmE2NjBhOWQ3ZjRmMDZmZDIiLCJFbWFpbCI6ImFkbWluQGVtYWlsLmNvbSIsIlJvbGUiOiJhZG1pbiJ9.kkcnAqajjcx0YmtRnWk-P594v_2wIEObwUzTtuMq_JY
