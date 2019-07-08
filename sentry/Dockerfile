ARG sentry_version=latest

FROM sentry:${sentry_version}

RUN PSYCOPG=$(pip freeze | grep psycopg2) \
	&& pip uninstall -y $PSYCOPG \
	&& pip install --no-binary :all: $PSYCOPG

RUN pip install https://github.com/getsentry/sentry-auth-github/archive/master.zip
