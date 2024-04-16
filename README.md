# SSH Ubuntu Server Dockerfile

These two dockerfiles create two ubuntu servers, one with SSH key auth and one with password auth.

### Add authorized keys

1. Create a file `authorized_keys`

2. Add something like below (your public keys)

```
# A key with pass phrase: password
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCvcA65iv9vuwbJpDCxzY5NjKn5pSubCIGEruK0vA28C80km3+35FtUaC7se4iH9CGLXn9k6zhBy1KxIHRB5nIOAhQBrDvSwWOXOJN+jfDv65Qr3WTX1tNKFrKjxZUbPTOtbmKkmYHB1yh61lmzp+HQ/K/g0Vane0nk9a+/6CHTtZWgUxiFMxeFz8havgIz1xufcn12RsqCzTvXa0kV64s9pKy1fW7b+/hq0xMuybEteiv2/P2kquryQI85DJOjNgYGHlrTG6bzDSJwwlBJCLYXLNWpuzOpV2SFBnkbg1NYtsgzGv2+l0cZnNV/w8NZuKQlJ+zXYklDpA6m9jJvAXYaiCPbK6bPvweL6CADxkd9zBL9KPTmiw6zPlH4A/VcRRwyDO2qZ7yOPkvpv5cGjlmeflEr4sw9DCmmg30Gh0/wN0GoFe+u0aFsperXh4LIzq+w89x8xeNM8M3GD8b8k0PLbg14r4+tdCa6lCxAPvO+jHr7tJBNRjAQ5VymMBu+Ir8= root@4e5b5dcb87b3

# A key without pass phrase
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCv3rsJsk3oHZVTrOIACUID63HKQSCqfIaAt3bYYKKu31RzFO0fukDpiUE4yKRUJ6of0dFap83pKEOL44pURQMNPRu4eHgtzxmh+yeiRvU0ZHgDBY0+1yU06Z7YgVSOWhu0sDqlI6zTpxYc81C2Nqw2Sp+ktsvY2yL2p4brQHbaZ2O5YRszfuIPbmCqKdL6oKs6CA0rvF3AXwcwUNRWO/eDZuiJvBMJE9nG/oHru3AnH/W4xhDikMZTGjf5fNphwsAuQT7D41FP5PWfjtL0I3CjkWr0HHCUYrj+dPzgAbHduR5axQdTxESEyL+5Efx39r2s+6qDFRfsOftXGB9Ln9yp40ejTo7W1x90RB3RSujRdROMnObFSwFcvgz1Z3oYxsWTOcdH0e8n9TYmr8Unn58dWr9zKIw7NijxVPsq7ND/hOOg9m6KkE+b/HDxiETaDw3NnkE3JiWyPqNNgiHdDDbXiNnp22bpIUqO2XwipA/ARRN/v5FhttO35ASbN7tiGN8= root@2118211552b9

```

### Build

```shell
docker build . -f SSHPassAuth.dockerfile -t ubuntu-ssh-password
```

```shell
docker build . -f SSHKeyAuth.dockerfile -t ubuntu-ssh-key
```

### Run the containers

```shell
docker run -d -p 5100:22 --name ubuntu-ssh ubuntu-ssh-password
```

Now you can ssh to the container using port 5100

```shell
ssh root@127.0.0.1 -p 5100

# the default password is root
```
