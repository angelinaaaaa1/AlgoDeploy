# Algorand Private Network Deployment

1. Install go-algorand following the instructions.
2. Generate a network template, e.g.
   `python3 template-gen.py 4 >lbvrf-4.json` (this generates a 4-node private network template)
3. Create data folders in a single machine:
   `goal network create -n lbvrf-stable -t lbvrf-4.json -r ./lbvrf-stable`
4. Rsync `lbvrf-stable` to all distributed machines
5. In the primary machine, run:
   `goal node start -d ./lbvrf-stable`
   Now go to `/lbvrf-stable/Primary` folder, the primary node gossip network address and port contained in `algod-listen.net` in the form of:
   `address:port`
6. In each other machine, say node 2, run:
   `goal node start -d ./lbvrf-stable -p address:port`
 
