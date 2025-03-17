# CLI Node Run Full Guide (PC and VPS for Both)

### Offical Docs by Pipe Network - https://docs.pipe.network/devnet-2

1️⃣ Dependencies for WINDOWS & LINUX & VPS
```
sudo apt update
sudo apt upgrade -y
```

For VPS Only
```
apt install screen -y
```

2️⃣ Download Some Files
```
curl -L -o pop "https://dl.pipecdn.app/v0.2.8/pop"
```
```
chmod +x pop
```

For VPS Only
```
screen -S pipe
```

3️⃣ Make Directory (create folder to be used for download cache)
```
mkdir download_cache
```

4️⃣ Signup Your Account
```
./pop --signup-by-referral-route d2be19523a45a241
```

```
# Generate Your Referral
./pop --gen-referral-route
```

5️⃣ Start Node
```
./pop --ram 8 --max-disk 500 --cache-dir /data --pubKey <KEY>
```

OR
```
./pop \

--ram 8 \              # RAM in GB

--max-disk 500 \       # Max disk usage in GB  

--cache-dir /data \    # Cache location

--pubKey <KEY>         # Solana public key (Address)
```

Note: Put your `ram` , `disk` & `pubkey` with your actual Information.Retrieve the public key from your Solana wallet (e.g., Phantom, Backpack) & Replace in `<KEY>` by Solana Address

![6165852026936868478](https://github.com/user-attachments/assets/6ceac486-a639-48ed-aa81-cccfbe02d6da)

If Your Node showing this Above Error then Put Below Command (Must Put `ram` , `disk` & `pubkey` value)
```
sudo ./pop --ram 8 --max-disk 500 --cache-dir /data --pubKey <KEY>
```

# Open Another Window for WSL or VPS

## Save the file
```
nano ~/node_info.json
```

## Monitor your Node Status & Points
```
./pop --status
```
```
./pop --points
```

## Check Points & Status from Dashboard - https://dashboard.pipenetwork.com/node-lookup


## 🔶For Next Day Run This Command

#1 Open WSL and Put this Command 
```
sudo ./pop --ram 8 --max-disk 500 --cache-dir /data --pubKey <KEY>
```

Note: Replace your `ram` , `disk` & `pubkey` with your actual Information.Retrieve the public key from your Solana wallet (e.g., Phantom, Backpack)

## Upgrade Your Node in v0.2.8

1️⃣ Upgrade (Download Latest Version)
```
curl -L -o pop "https://dl.pipecdn.app/v0.2.8/pop"
```
```
chmod +x pop
```

2️⃣ Start Node
```
sudo ./pop --ram 8 --max-disk 500 --cache-dir /data --pubKey <KEY>
```

Note: Put your `ram` , `disk` & `pubkey` with your actual Information.Retrieve the public key from your Solana wallet (e.g., Phantom, Backpack) & Replace in `<KEY>` by Solana Address

## Need to Free Your 8003 Port

### Identify the Process Using Port 8003
```
sudo ss -tulpn | grep 8003
```

Example - ``` LISTEN  0  128  0.0.0.0:0380  0.0.0.0:*  users:(("nginx",pid=1234,fd=6)) ```

### Terminate the Process by PID
```
sudo kill -9 1234
```

### Kill All Processes Using Port 8003
```
sudo fuser -k 8003/tcp
```

Reference Video How to Free 8003 or any port - https://youtu.be/4iP4GvLfCrU?t=229

## Delete Pipe node
```
cd /data
rm -f pop  # Deletes the 'pop' binary  
rm -rf download_cache  # Deletes the 'download_cache' folder  
rm -f node_info.json  # Deletes the 'node_info.json' file
```
