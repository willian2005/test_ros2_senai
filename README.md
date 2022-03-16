# test_ros2_senai


## Requisitos
1. Docker Engine
2. Docker Compose

## Compilando o container  

docker build . --tag test_ros2

## Iniciar contêiner
Execute o comando `docker-compose up`    
Em outra janela utilize o comando `docker exec -it <nome_da_execucao_do_container> bash` para acessar o container    
  

## Detalhes do docker
**Docker run**  

Para execultar o container utilizando o docker é necessário utilizar o seguinte comando  

`docker run --gpus all  --privileged=true -e DISPLAY=:0  --env="LIBGL_ALWAYS_INDIRECT=1" -e XDG_RUNTIME_DIR=/tmp -v $XDG_RUNTIME_DIR:/tmp/  --env QT_X11_NO_MITSHM="1" -e LIBGL_DEBUG="verbose" -v="/tmp/.X11-unix:/tmp/.X11-unix:rw"  -v /dev:/dev -it  ros2_ros2_senai`

**Docker compose**  

Para execultar o container com o `docker-compose up` é necessário utilizar uma versão posterior a 1.28, a partir desta versão foi habilitado utilização de GPU no docker compose

`https://docs.docker.com/compose/gpu-support/`

Como instalar  
`https://docs.docker.com/compose/install/`
