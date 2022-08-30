[[_ intro Python Docker]]

[[6 - Creating Container Images]]



---
# ENTRYPOINT & CMD
#docker/entrypoint   #docker/cmd

`ENTRYPOINT ["command", "opt1"]`
`CMD["opt2", "arg"]`
_start-up Command_=`command opt1 opt2 arg`

- `ENTRYPOINT` and `CMD` may have zero, one or more elements,
- start-up command must have one or more elements, first must be an executable
- both can be overridden at container creation (`CMD` is easy to be overridden)

## shell form vs Exec Form
`CMD flask run -h 0.0.0.0:5000`
`CMD ["flask", "run, "-h", "0:5000"]`
_start-upCommand_ = `flask run -h 0.0.0.0:5000`

- shell form uses linux shell process to execute a command line in a subprocess
- `/bin/sh` must be present in image filesystem
- avoid ENTRYPOINT in Shell Form


## overriding ENTRYPOINT
`ENTRYPOINT ["python", "manage.py"]`
`CMD ["runserver", "0.0.0.0:8000]`

`docker run .. --entrypoint bash myimage`
`bash` is final ENTRYPOINT
_start-upCommand_ = `bash`
CMD from Dockerfile is ignored

## overriding CMD
`ENTRYPOINT ["python", "manage.py"]`
`CMD ["runserver", "0.0.0.0:8000]`

`docker run .. myimage migrate`
`migrate` is finale CMD
_start-upCommand_=`python manage.py migrate`

-`# ENTRYPOINT[]`
`CMD["python", "color_boxes.py]`

`docker run ... myimage bash`
_start-upCommand_=`bahs`
`bash` id final CMD



















