# SCP

To copy a file from your pc to a remote user’s home:

```scp file.ext username@remote_ip:```

To copy a file from your pc to a specific existing directory on remote user’s home:

```scp file.ext username@remote_ip:project/```

To copy a folder use -r:

```scp -r project/ username@pi_ip_address:```
