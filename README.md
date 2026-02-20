<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Go REST API with Distroless Docker</title>
</head>
<body>

    <h1>Go REST API with Distroless Docker Image</h1>

    <p>
        This project demonstrates how to build and run a production-ready Go REST API
        using a multi-stage Docker build with a Distroless runtime image.
    </p>

    <hr>

    <h2>Project Overview</h2>

    <ul>
        <li><strong>Language:</strong> Go</li>
        <li><strong>Containerization:</strong> Docker</li>
        <li><strong>Build Strategy:</strong> Multi-stage build</li>
        <li><strong>Runtime Image:</strong> Distroless (Debian 12 base)</li>
        <li><strong>Security:</strong> Non-root container execution</li>
        <li><strong>Application Port:</strong> 5002</li>
    </ul>

    <hr>

    <h2>Build the Docker Image</h2>

    <pre>
docker build -t go-api-secure .
    </pre>

    <hr>

    <h2>Run the Container</h2>

    <pre>
docker run -d -p 5002:5002 --name secure-go-api go-api-secure
    </pre>

    <p>
        The application will be available at:
    </p>

    <pre>
http://localhost:5002
    </pre>

    <hr>

    <h2>Stop and Remove Container</h2>

    <pre>
docker stop secure-go-api
docker rm secure-go-api
    </pre>

    <hr>

    <h2>Verify Running Container</h2>

    <pre>
docker ps
docker logs secure-go-api
    </pre>

    <hr>

    <h2>Expected API Response</h2>

    <p>When accessing the root endpoint:</p>

    <pre>
GET /
    </pre>

    <p>Response:</p>

    <pre>
{
  "message": "Hello from Go Docker API"
}
    </pre>

    <hr>

    <h2>Security and Production Notes</h2>

    <ul>
        <li>The container runs as a non-root user.</li>
        <li>The runtime image does not include a shell or package manager.</li>
        <li>The image size is optimized using a multi-stage build.</li>
        <li>The attack surface is minimized by using a Distroless base image.</li>
    </ul>

</body>
</html>
