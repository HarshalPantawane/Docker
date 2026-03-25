# stage 1: build the application with all dependencies
FROM python:3.12 as builder    ##  use builder  for dependency 

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirement.txt

# stage 2: create a smaller image with only the necessary files 

FROM python:3.12-slim

WORKDIR /app

COPY --from=builder /usr/local/lib/python3.12 /usr/local/lib/python3.12

COPY . .

EXPOSE 5000
CMD [ "python", "myapp.py" ]