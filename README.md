# stress-ng
Docker Container for stress-ng 


Examples

stress-ng --cpu 4 --io 2 --vm 1 --vm-bytes 256M --timeout 60s

stress-ng --cpu 8 --cpu-ops 800000

stress-ng --cpu 4 --io 2 --timeout 60s --metrics

VM specific stress methods

These can be specified using the --vm-method option

stress-ng --vm 32 --vm-bytes 64M --vm-stride 1K --vm-populate --page-in --metrics-brief --times --timeout 60s

More Examples

stress-ng --fork 4 --fork-ops 100000

stress-ng --all 4 --timeout 5m

stress-ng --random 64

Check Stress-NG documentation for more details.
