Ansible Role: Kubernetes prep
=========

Prepare Ubuntu hosts for inclusion in a Kubernetes cluster.

Requirements
------------

None

Role Variables
--------------

When defining the Kubernetes version, you can get a list of available releases using apt-cache. For example,
to find all the point releases for Kubernetes 1.25 train: `apt-cache madison kubeadm | grep 1.25`

    # Kubernetes binary versions to install
    k8sversion: "1.25.6-00"

    # Docker GPG key URL, required for installing containerd
    docker_gpg_url: "https://download.docker.com/linux/ubuntu/gpg"

    # Kubernetes GPG key URL
    k8s_gpg_url: "https://packages.cloud.google.com/apt/doc/apt-key.gpg"

Dependencies
------------

None.

Example Playbook
----------------

    # ===========================================================================
    # Kubernetes pre-install tasks
    # ===========================================================================
    - name: Kubernetes pre-install tasks
      hosts: servers
      tags: k8s

      vars_files:
        # Ansible vault with all required passwords
        - "../../credentials.yml"

      roles:
        - jedimt.kubernetes_prep

License
-------

MIT

Author Information
------------------

Aaron Patten
aaronpatten@gmail.com
