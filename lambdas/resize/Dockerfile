FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# Copy pyproject.toml for dependency management
COPY pyproject.toml ./

# Synchronize dependencies using uv
RUN uv sync

# Copy the Lambda handler code
COPY handler.py ./

RUN uv sync --locked --no-install-project --no-editable

RUN python -m pip install --no-cache-dir pillow

RUN python -m pip install --no-cache-dir boto3

# Set the Lambda handler entry point
CMD ["handler.resize_handler"]
