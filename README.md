name: Pull Docker image and run container
  hosts: db
  become: true

  tasks:
    - name: Pull image from Docker Hub
      community.docker.docker_image:
        name: cammey20/ici-hyd
        source: pull

    - name: Run DB container
      community.docker.docker_container:
        name: db
        image: cammey20/ici-hyd
        state: started
        restart_policy: alway# ici-dev
