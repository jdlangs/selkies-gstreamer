# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at https://mozilla.org/MPL/2.0/.

FROM python:3-alpine

ARG PIP_BREAK_SYSTEM_PACKAGES=1
RUN pip3 install --no-cache-dir --force-reinstall flask

COPY app.py /etc

WORKDIR /etc

# Replace environment with customized TURN server
ENV TURN_SHARED_SECRET openrelayprojectsecret
ENV TURN_HOST staticauth.openrelay.metered.ca
ENV TURN_PORT 443
ENV TURN_PROTOCOL udp
ENV TURN_TLS false

EXPOSE 8008

CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0", "--port=8008"]
