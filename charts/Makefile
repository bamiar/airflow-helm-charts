PROJECT_ID=inspiring-rite-199401
REGISTRY=asia-northeast3-docker.pkg.dev
REPO=container-registry
APP= airflow-gke-dev
build: develop

develop:
	gcloud builds submit --config=develop.yaml --region=asia-northeast3 --substitutions=_PROJECT_ID="$(PROJECT_ID)",_REGISTRY="$(REGISTRY)",_REPO="$(REPO)",_APP="$(APP)" --gcs-log-dir=gs://inspiring-rite-199401_cloudbuild/airflow-gke-helm_log
	gcloud container clusters get-credentials airflow-gke-dev --region asia-northeast3 --project inspiring-rite-199401
	helm uninstall airflow-gke-dev --namespace airflow-gke-dev-01
	helm install -f ./airflow/values-dev.yaml airflow-gke-dev ./airflow --namespace airflow-gke-dev-01


# ImportError: cannot import name '_app_ctx_stack' from 'flask' (/home/airflow/.local/lib/python3.8/site-packages/flask/__init__.py)

# AirflowConfigException("webserver.base_url conf cannot have a trailing slash.") airflow.exceptions.AirflowConfigException: webserver.base_url conf cannot have a trailing slash.

# 상태: Does not have minimum availability airflow-gke-dev-db-migrations
# Pod errors: CrashLoopBackOff
# flask 2.1.13 provoke No module named 'flask.json.provider' error
# import AirflowJsonProvider File "/home/airflow/.local/lib/python3.8/site-packages/airflow/utils/json.py", line 25, in <module> from flask.json.provider import JSONProvider ModuleNotFoundError: No module named 'flask.json.provider'
#### Dockerfile에 RUN pip install flask-json 추가

# [CRITICAL] default fernet encryption key value!
#   * HELP: set a custom value with `airflow.fernetKey` or `AIRFLOW__CORE__FERNET_KEY`
# [CRITICAL] default webserver secret_key value!
#   * HELP: set a custom value with `airflow.webserverSecretKey` or `AIRFLOW__WEBSERVER__SECRET_KEY`
#
# [HIGH] using the embedded postgres database is NOT suitable for production!
#   * HELP: use an external postgres/mysql database with `externalDatabase.*`
# [MEDIUM] the scheduler "task creation check" is disabled, the scheduler may not be restarted if it deadlocks!
#   * HELP: configure the check with `scheduler.livenessProbe.taskCreationCheck.*`
####

#Error: INSTALLATION FAILED: An error occurred while checking for chart dependencies.
# You may need to run `helm dependency build` to fetch missing dependencies: found in Chart.yaml,
####helm dependency build 해당 경로에서 실행



