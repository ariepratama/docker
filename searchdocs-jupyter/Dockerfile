FROM python:3.12.3 as build

ENV WORKDIR=/opt/jupyter
WORKDIR /opt/jupyter
ADD ./requirements.txt /tmp/requirements.txt

RUN python -m venv "${WORKDIR}/venv"
ENV PATH="${WORKDIR}/venv/bin:$PATH"

RUN pip install --no-cache-dir -r /tmp/requirements.txt

FROM python:3.12.3-slim as runtime

ENV WORKDIR=/opt/jupyter
WORKDIR /opt/jupyter
COPY --from=build  /opt/jupyter /opt/jupyter
ENV PATH="${WORKDIR}/venv/bin:$PATH"

CMD ["jupyter", "notebook", "--NotebookApp.token=''"]

