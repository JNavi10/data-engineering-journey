# How to run a python script inside a Docker Container

To run a python script we need to
1. Define the working directory
2. Copy the source code from the host machine to Docker Image
3. Set the command to execute the script when the container runs

## `WORKDIR` instruction

- Sets the working directory inside the container
- All following instructions use this directory as the current directory (like `cd`)
- Default is root directory which is not a good place to store apps

### Example
Most common workdir is `/app`
```dockerfile
WORKDIR /app
```


## `COPY` instruction

- The `COPY` instruction copies files or folders from your host machine into the image.
- If `WORKDIR` is specified it copies to that directory
- If files aren't copied, it can't be used

### Example
Copy all files
```dockerfile
COPY . .
```

## Sample Exercise

1. Update Dockerfile

    ```dockerfile
    FROM python:3.10
    RUN pip install pandas
    WORKDIR /app
    COPY sample.py .
    ENTRYPOINT ["python","sample.py"]
    ```

2. Create Sample Script

    ```python
    import sys
    import pandas as pd

    print('pandas successfully imported')

    arg =  sys.argv[1]

    print(f'command line argument is {arg}')
    ```

3. `cd` to dir where your new files are
4. Build and run
    ```bash
    docker build -t python3.10:pandas .
    
    docker run -it python3.10:pandas argument_1
    ```

You should get an output like this
```
pandas successfully imported
command line argument is argument_1
```

