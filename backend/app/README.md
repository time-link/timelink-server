# Development

Check the README.md in the top level directory of `timelink-server` 
repository which contains the original instructions of the stack
template. Here we clarify some aspects.

## Testing directly in the backend

The test are run inside the container. So it is necessary to 
connect to the container and run the tests from there.

```bash
docker-compose exec backend bash

# And you should get

root@dfd228cbdb2b:/app# 

```
Then at that prompt
```bash
DOMAIN=backend sh ./scripts/test.sh
```
And the first run after install should look like:
```bash
+ pytest --cov=app --cov-report=term-missing app/tests
=============================================== test session starts ===============================================
platform linux -- Python 3.7.12, pytest-5.4.3, py-1.10.0, pluggy-0.13.1
rootdir: /app
plugins: anyio-3.3.1, celery-4.4.7, cov-2.12.1
collected 25 items                                                                                                

app/tests/api/api_v1/test_celery.py .                                                                       [  4%]
app/tests/api/api_v1/test_items.py ..                                                                       [ 12%]
app/tests/api/api_v1/test_login.py ..                                                                       [ 20%]
app/tests/api/api_v1/test_users.py .......                                                                  [ 48%]
app/tests/crud/test_item.py ....                                                                            [ 64%]
app/tests/crud/test_user.py .........                                                                       [100%]

---------- coverage: platform linux, python 3.7.12-final-0 -----------
Name                                   Stmts   Miss  Cover   Missing
--------------------------------------------------------------------
app/__init__.py                            0      0   100%
app/api/__init__.py                        0      0   100%
app/api/api_v1/__init__.py                 0      0   100%
app/api/api_v1/api.py                      7      0   100%
app/api/api_v1/endpoints/__init__.py       0      0   100%
app/api/api_v1/endpoints/items.py         42     20    52%   22-28, 56-62, 77, 79, 93-99
app/api/api_v1/endpoints/login.py         47     21    55%   33, 35, 58-69, 81-96
app/api/api_v1/endpoints/users.py         63     25    60%   66-75, 100-113, 127, 129, 146-153
app/api/api_v1/endpoints/utils.py         16      2    88%   34-35
app/api/deps.py                           34      4    88%   35-36, 42, 50
app/backend_pre_start.py                  21     21     0%   1-37
app/celeryworker_pre_start.py             21     21     0%   1-37
app/core/__init__.py                       0      0   100%
app/core/celery_app.py                     3      0   100%
app/core/config.py                        59      5    92%   22, 25, 33, 45, 66
app/core/security.py                      18      1    94%   21
app/crud/__init__.py                       2      0   100%
app/crud/base.py                          39      6    85%   35-40
app/crud/crud_item.py                     17      1    94%   25
app/crud/crud_user.py                     36      2    94%   31, 45
app/db/__init__.py                         0      0   100%
app/db/base.py                             3      3     0%   3-5
app/db/base_class.py                       8      0   100%
app/db/init_db.py                          9      9     0%   1-25
app/db/session.py                          5      0   100%
app/initial_data.py                       14     14     0%   1-22
app/main.py                                8      0   100%
app/models/__init__.py                     2      0   100%
app/models/item.py                        12      1    92%   9
app/models/user.py                        14      1    93%   9
app/schemas/__init__.py                    4      0   100%
app/schemas/item.py                       19      0   100%
app/schemas/msg.py                         3      0   100%
app/schemas/token.py                       7      0   100%
app/schemas/user.py                       20      0   100%
app/tests/__init__.py                      0      0   100%
app/tests/api/__init__.py                  0      0   100%
app/tests/api/api_v1/__init__.py           0      0   100%
app/tests/api/api_v1/test_celery.py        8      0   100%
app/tests/api/api_v1/test_items.py        22      0   100%
app/tests/api/api_v1/test_login.py        15      0   100%
app/tests/api/api_v1/test_users.py        73      0   100%
app/tests/conftest.py                     22      0   100%
app/tests/crud/__init__.py                 0      0   100%
app/tests/crud/test_item.py               52      0   100%
app/tests/crud/test_user.py               75      0   100%
app/tests/utils/__init__.py                0      0   100%
app/tests/utils/item.py                   14      0   100%
app/tests/utils/user.py                   30      2    93%   44-45
app/tests/utils/utils.py                  16      0   100%
app/tests_pre_start.py                    21     21     0%   1-37
app/utils.py                              54     23    57%   37-41, 50-56, 91-98, 102-106
app/worker.py                              7      7     0%   1-11
--------------------------------------------------------------------
TOTAL                                    962    210    78%


=============================================== 25 passed in 11.32s ===============================================
root@dfd228cbdb2b:/app# 

```

## Testing backend from the development machine shell

Tests can also be run from the development machine shell.

In the top level directory of the project do:

```console
DOMAIN=backend sh ./scripts/test.sh
```


```console
% DOMAIN=backend sh ./scripts/test.sh

...

Building backend
[+] Building 1.2s (12/12) 
FINISHED                                                                                                  

...

Creating network "timelink-server_default" with the default driver
Creating network "timelink-server_traefik-public" with the default driver
Creating volume "timelink-server_app-db-data" with default driver

...

INFO:__main__:Service finished initializing
+ pytest --cov=app --cov-report=term-missing app/tests
============================= test session starts ==============================
platform linux -- Python 3.7.12, pytest-5.4.3, py-1.10.0, pluggy-0.13.1
rootdir: /app
plugins: cov-2.12.1, celery-4.4.7
collected 25 items

app/tests/api/api_v1/test_celery.py .                                    [  4%]
app/tests/api/api_v1/test_items.py ..                                    [ 12%]
app/tests/api/api_v1/test_login.py ..                                    [ 20%]
app/tests/api/api_v1/test_users.py .......                               [ 48%]
app/tests/crud/test_item.py ....                                         [ 64%]
app/tests/crud/test_user.py .........                                    [100%]

---------- coverage: platform linux, python 3.7.12-final-0 -----------
Name                                   Stmts   Miss  Cover   Missing
--------------------------------------------------------------------
app/__init__.py                            0      0   100%
app/api/__init__.py                        0      0   100%
app/api/api_v1/__init__.py                 0      0   100%
app/api/api_v1/api.py                      7      0   100%
app/api/api_v1/endpoints/__init__.py       0      0   100%
app/api/api_v1/endpoints/items.py         42     20    52%   22-28, 56-62, 77, 79, 93-99
app/api/api_v1/endpoints/login.py         47     21    55%   33, 35, 58-69, 81-96
app/api/api_v1/endpoints/users.py         63     26    59%   48, 66-75, 100-113, 127, 129, 146-153
app/api/api_v1/endpoints/utils.py         16      2    88%   34-35
app/api/deps.py                           34      4    88%   35-36, 42, 50
app/backend_pre_start.py                  21     21     0%   1-37
app/celeryworker_pre_start.py             21     21     0%   1-37
app/core/__init__.py                       0      0   100%
app/core/celery_app.py                     3      0   100%
app/core/config.py                        59      5    92%   22, 25, 33, 45, 66
app/core/security.py                      18      1    94%   21
app/crud/__init__.py                       2      0   100%
app/crud/base.py                          39      6    85%   35-40
app/crud/crud_item.py                     17      1    94%   25
app/crud/crud_user.py                     36      2    94%   31, 45
app/db/__init__.py                         0      0   100%
app/db/base.py                             3      3     0%   3-5
app/db/base_class.py                       8      0   100%
app/db/init_db.py                          9      9     0%   1-25
app/db/session.py                          5      0   100%
app/initial_data.py                       14     14     0%   1-22
app/main.py                                8      0   100%
app/models/__init__.py                     2      0   100%
app/models/item.py                        12      1    92%   9
app/models/user.py                        14      1    93%   9
app/schemas/__init__.py                    4      0   100%
app/schemas/item.py                       19      0   100%
app/schemas/msg.py                         3      0   100%
app/schemas/token.py                       7      0   100%
app/schemas/user.py                       20      0   100%
app/tests/__init__.py                      0      0   100%
app/tests/api/__init__.py                  0      0   100%
app/tests/api/api_v1/__init__.py           0      0   100%
app/tests/api/api_v1/test_celery.py        8      0   100%
app/tests/api/api_v1/test_items.py        22      0   100%
app/tests/api/api_v1/test_login.py        15      0   100%
app/tests/api/api_v1/test_users.py        73      0   100%
app/tests/conftest.py                     22      0   100%
app/tests/crud/__init__.py                 0      0   100%
app/tests/crud/test_item.py               52      0   100%
app/tests/crud/test_user.py               75      0   100%
app/tests/utils/__init__.py                0      0   100%
app/tests/utils/item.py                   14      0   100%
app/tests/utils/user.py                   30      2    93%   47-48
app/tests/utils/utils.py                  16      0   100%
app/tests_pre_start.py                    21     21     0%   1-37
app/utils.py                              54     40    26%   19-33, 37-41, 50-56, 71-76, 91-98, 102-106
app/worker.py                              7      7     0%   1-11
--------------------------------------------------------------------
TOTAL                                    962    228    76%


============================= 25 passed in 13.86s ==============================
WARNING: The following deploy sub-keys are not supported and have been ignored: labels

...
Stopping timelink-server_celeryworker_1 ... done
Stopping timelink-server_pgadmin_1      ... done
...
Removing timelink-server_frontend_1     ... done
Removing network timelink-server_default
Removing network timelink-server_traefik-public
Removing volume timelink-server_app-db-data
% 
```