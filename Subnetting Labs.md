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

## Exercise 5 — divide a /24 into /28 subnets

A `/28` has 16 total addresses and a block size of 16 in the final octet. The subnet network addresses are `.0`, `.16`, `.32`, `.48`, and so on. For a conventional subnet, each block has a network address and broadcast address, leaving 14 usable host addresses.

## Exercise 6 — variable-length prefixes

Compare `/24`, `/26`, `/27`, and `/28`. As the prefix length increases, the network portion grows and the number of host bits decreases. This creates smaller subnets and more possible subnet boundaries.

## Verification method

Calculate the prefix and block size manually before using a subnet calculator. Check that the selected host address falls between the network and broadcast addresses. Be aware of special cases such as `/31` point-to-point links and `/32` host routes.

## My understanding

Create two subnets from a `/24` address block for two lab segments. Show the network address, prefix, broadcast address, and conventional usable host range for each. Ensure the subnets do not overlap.
