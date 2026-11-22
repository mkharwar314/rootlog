# Subnetting Labs

> Practice calculating IPv4 subnet ranges and checking your answers.

## Method

For a prefix `/p`:
- Host bits = `32 - p`.
- Total addresses = `2^(host bits)`.
- In a conventional IPv4 subnet, network and broadcast addresses are not assigned to hosts (with special cases such as `/31` point-to-point links and `/32` host routes).

## Exercise 1

Network: `192.168.10.0/24`

- Subnet mask: `255.255.255.0`
- Total addresses: 256
- Conventional usable hosts: 254
- Network: `192.168.10.0`
- Broadcast: `192.168.10.255`

## Exercise 2

Network: `192.168.10.0/26`

- Subnet mask: `255.255.255.192`
- Block size in final octet: 64
- Subnets begin at .0, .64, .128, and .192.
- Each subnet contains 64 addresses; conventional usable hosts: 62.

## Exercise 3

Find the network, broadcast, and usable host range for `192.168.10.77/27`.

Answer:
- Block size: 32.
- Containing subnet: `192.168.10.64/27`.
- Broadcast: `192.168.10.95`.
- Conventional usable range: `192.168.10.65`–`192.168.10.94`.

## Exercise 4

How many addresses are in a `/28`? How many conventional usable hosts?

Answer: 16 total, 14 conventional usable hosts.

## Practical verification

Use a subnet calculator only after doing the calculation manually. Compare results and explain any discrepancy.

## Completion criteria

You can calculate the mask, block size, network address, broadcast address, and host range for common prefixes.
