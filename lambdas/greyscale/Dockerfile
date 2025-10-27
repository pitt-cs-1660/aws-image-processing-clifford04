FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

COPY pyproject.toml ./

RUN uv sync

COPY handler.py ./

RUN uv sync --locked --no-install-project --no-editable

RUN python -m pip install --no-cache-dir pillow

RUN python -m pip install --no-cache-dir boto3

CMD ["handler.greyscale_handler"]

############
#
# TODO: implement the rest of the image
#
############
