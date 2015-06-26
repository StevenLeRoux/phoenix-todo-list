# api

The dwyl REST &amp; WebSocket API.

![perfection-intro-image](https://cloud.githubusercontent.com/assets/194400/8255483/2fc78e6c-1698-11e5-8c27-d1b9db99f020.png)

## Run the API Locally

You will need a running instance of ElasticSearch for this API to work on your localhost.

Steps:
+ Learn Vagrant: https://github.com/docdis/learn-vagrant
+ Start Vagrant VM with ElasticSearch `vagrant up`
+ Start API server: `npm install && npm start`

## Send Welcome Email

### Local

```sh
curl --data "email=dwyl.smith+1234@gmail.com" http://localhost:1337/email
```

### heroku

```
curl --data "email=dwyl.smith+1234@gmail.com" https://dwylapi.herokuapp.com/email
```


## *Expected* Environment Variables˜

The API server will *not* work unless these
environment variables are set.

Run the following command to set up your local machine:
```sh
export ES_INDEX=dwyl
export MANDRILL_APIKEY='AskUsForTheKey!'

```


## Troubleshooting

Get list of records in ES:

```sh
curl -XGET 'localhost:9200/dwyl/_search?search_type=scan&scroll=10m&size=50' -d '
{
    "query" : {
        "match_all" : {}
    }
}'
```

## Pushing changes from master to Heroku
+ Make sure your local copy of the `master` branch is up-to-date and passing every test with 100% coverage
+ Check whether you already have a heroku remote by running `git remote -v` in the command line
  + If you do, you should see something like this:
  ![heroku remote](https://cloud.githubusercontent.com/assets/4185328/8380179/513ad458-1c1c-11e5-9ec4-a279861da254.png)
  + Otherwise, you need to set up a remote (in this case named heroku) using `git remote add heroku <gitURL>` where you enter the Heroku's Git URL (you can find it in the settings) inside the angle brackets
+ Push to heroku as standard: `git push heroku master`

**Note: _You can only only do this if you have collaborator access in heroku._**
  