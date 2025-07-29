    FROM python:3.12.0-slim-bookworm

    ENV PYTHONBUFFERED=1
    ENV PYTHONWRITEBYTECODE=1
    ENV APP=/app

    # Change the workdir
    WORKDIR $APP

    # Install the requirements
    COPY requirements.txt $APP
    RUN pip3 install -r requirements.txt

    # Copy the rest of the files
    COPY . $APP

    EXPOSE 8000

    # Give permission to entrypoint script
    RUN chmod +x /app/entrypoint.sh

    # Entrypoint script that runs migrations
    ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]

    # Gunicorn command
    CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]
