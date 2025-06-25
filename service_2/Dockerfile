FROM python:3.13-slim-bookworm

WORKDIR /source

#COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv
#COPY --from=ghcr.io/astral-sh/uv:latest /uvx /bin/uvx

RUN apt-get update && \
    apt-get install -y curl build-essential git && \
    pip install --no-cache-dir uv

ENV VIRTUAL_ENV=/source/.venv
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

COPY pyproject.toml uv.lock ./

RUN uv venv .venv && uv pip install .

COPY . .

EXPOSE 8000

CMD ["uv", "run", "app.py"]
