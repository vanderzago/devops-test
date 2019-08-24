FROM python:alpine

COPY src/frontend /app

WORKDIR /app

RUN pip install -r requirements.txt

ENTRYPOINT ["python"]

CMD ["frontend.py"]

EXPOSE 8000