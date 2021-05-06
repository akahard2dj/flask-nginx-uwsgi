# flask-nginx-uwsgi

```console
foo@bar:~$ sudo docker-compose up -d --build
Creating network "flask-nginx-uwsgi_default" with the default driver
Building flask
Step 1/5 : FROM python:3
3: Pulling from library/python
bd8f6a7501cc: Pull complete
44718e6d535d: Pull complete
efe9738af0cb: Pull complete
f37aabde37b8: Pull complete
3923d444ed05: Pull complete
1ecef690e281: Pull complete
1c053581d9c9: Pull complete
81182ea718cf: Pull complete
83ebd4edf9af: Pull complete
Digest: sha256:0813df59b3d73a13fc581fd416d7733a2de6540d7e3f7633a1a9aabf9b201548
Status: Downloaded newer image for python:3
 ---> 70aa8983ec5c
Step 2/5 : WORKDIR /app
 ---> Running in 4588a4ff61ee
Removing intermediate container 4588a4ff61ee
 ---> 5cf9e2162705
Step 3/5 : ADD . /app
 ---> c85ab9f48d90
Step 4/5 : RUN pip install -r requirements.txt
 ---> Running in aa148e24d7a0
Collecting Flask
  Downloading Flask-1.1.2-py2.py3-none-any.whl (94 kB)
Collecting uWSGI
  Downloading uWSGI-2.0.19.1.tar.gz (803 kB)
Collecting itsdangerous>=0.24
  Downloading itsdangerous-1.1.0-py2.py3-none-any.whl (16 kB)
Collecting Jinja2>=2.10.1
  Downloading Jinja2-2.11.3-py2.py3-none-any.whl (125 kB)
Collecting click>=5.1
  Downloading click-7.1.2-py2.py3-none-any.whl (82 kB)
Collecting Werkzeug>=0.15
  Downloading Werkzeug-1.0.1-py2.py3-none-any.whl (298 kB)
Collecting MarkupSafe>=0.23
  Downloading MarkupSafe-1.1.1-cp39-cp39-manylinux2010_x86_64.whl (32 kB)
Building wheels for collected packages: uWSGI
  Building wheel for uWSGI (setup.py): started
  Building wheel for uWSGI (setup.py): finished with status 'done'
  Created wheel for uWSGI: filename=uWSGI-2.0.19.1-cp39-cp39-linux_x86_64.whl size=583515 sha256=cf61d015aafd14d560c1a5337283c5e4778016b86797061e24657d7dfe154330
  Stored in directory: /root/.cache/pip/wheels/17/66/cf/112237fefe0b8011e4a481305ba799b696ece8590219bd527f
Successfully built uWSGI
Installing collected packages: MarkupSafe, Werkzeug, Jinja2, itsdangerous, click, uWSGI, Flask
Successfully installed Flask-1.1.2 Jinja2-2.11.3 MarkupSafe-1.1.1 Werkzeug-1.0.1 click-7.1.2 itsdangerous-1.1.0 uWSGI-2.0.19.1
WARNING: Running pip as root will break packages and permissions. You should install packages reliably by using venv: https://pip.pypa.io/warnings/venv
Removing intermediate container aa148e24d7a0
 ---> 4e3745b3612c
Step 5/5 : CMD ["uwsgi", "uwsgi.ini"]
 ---> Running in 63f26b6ddf06
Removing intermediate container 63f26b6ddf06
 ---> 6b84eb1961cc

Successfully built 6b84eb1961cc
Successfully tagged flask-nginx-uwsgi_flask:latest
Building nginx
Step 1/3 : FROM nginx
latest: Pulling from library/nginx
f7ec5a41d630: Already exists
aa1efa14b3bf: Pull complete
b78b95af9b17: Pull complete
c7d6bca2b8dc: Pull complete
cf16cd8e71e0: Pull complete
0241c68333ef: Pull complete
Digest: sha256:75a55d33ecc73c2a242450a9f1cc858499d468f077ea942867e662c247b5e412
Status: Downloaded newer image for nginx:latest
 ---> 62d49f9bab67
Step 2/3 : RUN rm /etc/nginx/conf.d/default.conf
 ---> Running in f2d856074351
Removing intermediate container f2d856074351
 ---> a96fc1e107e2
Step 3/3 : COPY nginx.conf /etc/nginx/conf.d/

Successfully built 8d4c7a26c875
Creating flask ... done
Creating nginx ... done
```
