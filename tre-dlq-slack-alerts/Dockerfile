FROM public.ecr.aws/lambda/python:3.9
ARG PIP_INDEX_URL

# Copy function code
COPY tre_dlq_slack_alerts.py ${LAMBDA_TASK_ROOT}

# Install the function's dependencies using file requirements.txt
COPY requirements.txt ./requirements.txt
RUN  yum -y update \
     && yum clean all \
     && pip install \
       --requirement requirements.txt \
       --target "${LAMBDA_TASK_ROOT}"

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "tre_dlq_slack_alerts.lambda_handler" ]
