# SSH

## One-liner to remove entry in `~/.ssh/known_hosts`

Let say you remap a domain DNS to another server, the server fingerprint will change and your local ssh client will scream at you. 
In this one-liner we remove the line 64 from our local `.ssh/known_hosts`, which is the one containing the fingerprint from the previous server.

```bash
sed -i -e '64d' .ssh/known_hosts
```
