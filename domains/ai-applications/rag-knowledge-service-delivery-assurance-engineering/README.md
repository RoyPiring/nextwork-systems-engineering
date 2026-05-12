# RAG Knowledge Service Delivery Assurance Engineering

> Inside the [NextWork Systems Engineering](../../../README.md) portfolio · **4 validated build(s)**.

## Overview

This domain captures **4 validated build(s)** in rag knowledge service delivery assurance engineering. Each build is preserved in [`documents/`](./documents/) with the full source content, screenshots, and command outputs from when the system was completed end-to-end.

-T-h-i-s- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -h-o-w- -t-o- -b-u-i-l-d- -a- -R-e-t-r-i-e-v-a-l---A-u-g-m-e-n-t-e-d- -G-e-n-e-r-a-t-i-o-n- -(-R-A-G-)- -A-P-I- -u-s-i-n-g- -F-a-s-t-A-P-I- -t-o- -a-n-s-w-e-r- -u-s-e-r- -q-u-e-s-t-i-o-n-s- -b-a-s-e-d- -o-n- -a- -s-u-p-p-l-i-e-d- -s-e-t- -o-f- -f-i-l-e-s-.- -T-h-e- -g-o-a-l- -i-s- -t-o- -d-e-s-i-g-n- -a- -w-o-r-k-i-n-g- -A-I- -s-y-s-t-e-m- -t-h-a-t- -c-o-m-b-i-n-e-s- -r-e-t-r-i-e-v-a-l- -a-n-d- -g-e-n-e-r-a-t-i-o-n- -i-n-t-o- -a- -s-i-n-g-l-e-,- -r-e-u-s-a-b-l-e- -s-e-r-v-i-c-e- -r-a-t-h-e-r- -t-h-a-n- -a- -c-o-n-c-e-p-t-u-a-l- -e-x-a-m-p-l-e-.--
--
-T-h-e- -f-o-c-u-s- -i-s- -o-n- -u-n-d-e-r-s-t-a-n-d-i-n-g- -h-o-w- -R-A-G- -s-y-s-t-e-m-s- -f-u-n-c-t-i-o-n- -e-n-d- -t-o- -e-n-d-,- -s-t-r-e-n-g-t-h-e-n-i-n-g- -P-y-t-h-o-n- -a-n-d- -F-a-s-t-A-P-I- -s-k-i-l-l-s-,- -a-n-d- -p-r-o-d-u-c-i-n-g- -a- -p-r-a-c-t-i-c-a-l- -A-P-I- -t-h-a-t- -c-a-n- -b-e- -e-x-t-e-n-d-e-d- -o-r- -a-d-a-p-t-e-d- -f-o-r- -r-e-a-l---w-o-r-l-d- -u-s-e-.--
--
-
--
-T-h-e- -s-e-r-v-i-c-e-s- -u-s-e-d- -i-n- -t-h-i-s- -p-r-o-j-e-c-t- -a-r-e- -P-y-t-h-o-n-,- -F-a-s-t-A-P-I-,- -C-h-r-o-m-a-,- -U-v-i-c-o-r-n-,- -a-n-d- -O-l-l-a-m-a-.--
--
-P-y-t-h-o-n- -p-r-o-v-i-d-e-s- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -l-o-g-i-c- -a-n-d- -o-r-c-h-e-s-t-r-a-t-i-o-n- -l-a-y-e-r-.- -F-a-s-t-A-P-I- -i-s- -u-s-e-d- -t-o- -e-x-p-o-s-e- -t-h-e- -A-I- -s-y-s-t-e-m- -t-h-r-o-u-g-h- -a- -c-l-e-a-n- -a-n-d- -w-e-l-l---d-e-f-i-n-e-d- -A-P-I-.- -C-h-r-o-m-a- -s-e-r-v-e-s- -a-s- -t-h-e- -v-e-c-t-o-r- -d-a-t-a-b-a-s-e- -t-h-a-t- -e-n-a-b-l-e-s- -s-e-m-a-n-t-i-c- -s-e-a-r-c-h- -o-v-e-r- -t-h-e- -k-n-o-w-l-e-d-g-e- -b-a-s-e-.- -U-v-i-c-o-r-n- -r-u-n-s- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -a-s- -a-n- -A-S-G-I- -s-e-r-v-i-c-e-.- -O-l-l-a-m-a- -a-l-l-o-w-s- -t-h-e- -s-y-s-t-e-m- -t-o- -r-u-n- -a- -l-o-c-a-l- -l-a-n-g-u-a-g-e- -m-o-d-e-l- -w-i-t-h-o-u-t- -r-e-l-y-i-n-g- -o-n- -e-x-t-e-r-n-a-l- -c-l-o-u-d- -s-e-r-v-i-c-e-s-.--
--
-K-e-y- -c-o-n-c-e-p-t-s- -e-x-p-l-o-r-e-d- -i-n-c-l-u-d-e- -R-e-t-r-i-e-v-a-l---A-u-g-m-e-n-t-e-d- -G-e-n-e-r-a-t-i-o-n- -(-R-A-G-)-,- -v-e-c-t-o-r- -e-m-b-e-d-d-i-n-g-s-,- -s-e-m-a-n-t-i-c- -s-e-a-r-c-h-,- -A-P-I---b-a-s-e-d- -A-I- -s-y-s-t-e-m- -d-e-s-i-g-n-,- -a-n-d- -l-o-c-a-l- -L-L-M- -e-x-e-c-u-t-i-o-n-.--
--
-
--
-T-h-i-s- -p-r-o-j-e-c-t- -t-o-o-k- -a-p-p-r-o-x-i-m-a-t-e-l-y- -t-w-o- -h-o-u-r-s- -t-o- -c-o-m-p-l-e-t-e-.- -T-h-e- -p-r-i-m-a-r-y- -c-h-a-l-l-e-n-g-e- -w-a-s- -c-o-n-f-i-g-u-r-i-n-g- -t-h-e- -P-y-t-h-o-n- -v-i-r-t-u-a-l- -e-n-v-i-r-o-n-m-e-n-t- -a-n-d- -e-n-s-u-r-i-n-g- -t-h-a-t- -a-l-l- -d-e-p-e-n-d-e-n-c-i-e-s- -w-e-r-e- -i-n-s-t-a-l-l-e-d- -c-o-r-r-e-c-t-l-y- -a-n-d- -c-o-m-p-a-t-i-b-l-e- -w-i-t-h- -o-n-e- -a-n-o-t-h-e-r-.--
--
-T-h-e- -m-o-s-t- -r-e-w-a-r-d-i-n-g- -o-u-t-c-o-m-e- -w-a-s- -o-b-s-e-r-v-i-n-g- -t-h-e- -A-P-I- -c-o-n-s-i-s-t-e-n-t-l-y- -r-e-t-u-r-n- -a-c-c-u-r-a-t-e-,- -c-o-n-t-e-x-t---a-w-a-r-e- -a-n-s-w-e-r-s- -b-a-s-e-d- -o-n- -t-h-e- -k-n-o-w-l-e-d-g-e- -b-a-s-e-.- -T-h-i-s- -c-o-n-f-i-r-m-e-d- -t-h-a-t- -t-h-e- -r-e-t-r-i-e-v-a-l- -p-i-p-e-l-i-n-e- -a-n-d- -t-h-e- -l-o-c-a-l- -l-a-n-g-u-a-g-e- -m-o-d-e-l- -w-e-r-e- -f-u-n-c-t-i-o-n-i-n-g- -c-o-r-r-e-c-t-l-y- -t-o-g-e-t-h-e-r-.--
--
-
--
-I- -c-o-m-p-l-e-t-e-d- -t-h-i-s- -p-r-o-j-e-c-t- -t-o- -g-a-i-n- -h-a-n-d-s---o-n- -e-x-p-e-r-i-e-n-c-e- -b-u-i-l-d-i-n-g- -a- -R-A-G- -s-y-s-t-e-m- -f-r-o-m- -t-h-e- -g-r-o-u-n-d- -u-p- -r-a-t-h-e-r- -t-h-a-n- -r-e-l-y-i-n-g- -o-n- -m-a-n-a-g-e-d- -o-r- -a-b-s-t-r-a-c-t-e-d- -s-o-l-u-t-i-o-n-s-.- -T-h-e- -o-b-j-e-c-t-i-v-e- -w-a-s- -t-o- -u-n-d-e-r-s-t-a-n-d- -h-o-w- -r-e-t-r-i-e-v-a-l-,- -e-m-b-e-d-d-i-n-g-s-,- -a-n-d- -g-e-n-e-r-a-t-i-o-n- -i-n-t-e-r-a-c-t- -a-t- -r-u-n-t-i-m-e-.--
--
-B-y- -b-u-i-l-d-i-n-g- -t-h-i-s- -A-P-I-,- -I- -e-x-p-a-n-d-e-d- -m-y- -p-r-a-c-t-i-c-a-l- -e-x-p-e-r-i-e-n-c-e- -w-i-t-h- -P-y-t-h-o-n-,- -F-a-s-t-A-P-I-,- -v-e-c-t-o-r- -d-a-t-a-b-a-s-e-s-,- -a-n-d- -l-o-c-a-l- -L-L-M-s- -w-h-i-l-e- -p-r-o-d-u-c-i-n-g- -a- -f-u-n-c-t-i-o-n-a-l- -s-y-s-t-e-m- -t-h-a-t- -d-e-m-o-n-s-t-r-a-t-e-s- -h-o-w- -R-A-G- -i-m-p-r-o-v-e-s- -r-e-s-p-o-n-s-e- -a-c-c-u-r-a-c-y- -t-h-r-o-u-g-h- -g-r-o-u-n-d-e-d- -c-o-n-t-e-x-t-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -d-e-m-o-n-s-t-r-a-t-e-s- -h-o-w- -t-o- -c-o-n-t-a-i-n-e-r-i-z-e- -a- -R-e-t-r-i-e-v-a-l---A-u-g-m-e-n-t-e-d- -G-e-n-e-r-a-t-i-o-n- -(-R-A-G-)- -A-P-I- -u-s-i-n-g- -D-o-c-k-e-r-.- -T-h-e- -o-b-j-e-c-t-i-v-e- -i-s- -t-o- -p-a-c-k-a-g-e- -a-n- -e-x-i-s-t-i-n-g- -A-I- -a-p-p-l-i-c-a-t-i-o-n- -i-n-t-o- -a- -p-o-r-t-a-b-l-e-,- -r-e-p-r-o-d-u-c-i-b-l-e- -c-o-n-t-a-i-n-e-r- -t-h-a-t- -c-a-n- -r-u-n- -c-o-n-s-i-s-t-e-n-t-l-y- -a-c-r-o-s-s- -e-n-v-i-r-o-n-m-e-n-t-s-.--
--
-T-h-e- -f-o-c-u-s- -i-s- -o-n- -a-p-p-l-y-i-n-g- -D-o-c-k-e-r- -i-n- -a- -p-r-a-c-t-i-c-a-l- -D-e-v-O-p-s- -c-o-n-t-e-x-t- -w-h-i-l-e- -r-e-i-n-f-o-r-c-i-n-g- -h-o-w- -A-I- -s-y-s-t-e-m-s- -a-r-e- -p-r-e-p-a-r-e-d- -f-o-r- -d-e-p-l-o-y-m-e-n-t-.- -B-y- -c-o-n-t-a-i-n-e-r-i-z-i-n-g- -t-h-e- -R-A-G- -A-P-I-,- -t-h-i-s- -p-r-o-j-e-c-t- -b-r-i-d-g-e-s- -a-p-p-l-i-c-a-t-i-o-n- -d-e-v-e-l-o-p-m-e-n-t- -a-n-d- -o-p-e-r-a-t-i-o-n-a-l- -r-e-a-d-i-n-e-s-s-.--
--
-
--
-T-h-e- -s-e-r-v-i-c-e-s- -u-s-e-d- -i-n- -t-h-i-s- -p-r-o-j-e-c-t- -a-r-e- -F-a-s-t-A-P-I-,- -C-h-r-o-m-a-,- -U-v-i-c-o-r-n-,- -O-l-l-a-m-a-,- -a-n-d- -D-o-c-k-e-r-.--
--
-F-a-s-t-A-P-I- -p-r-o-v-i-d-e-s- -t-h-e- -A-P-I- -l-a-y-e-r-,- -C-h-r-o-m-a- -s-e-r-v-e-s- -a-s- -t-h-e- -v-e-c-t-o-r- -d-a-t-a-b-a-s-e- -f-o-r- -r-e-t-r-i-e-v-a-l-,- -U-v-i-c-o-r-n- -r-u-n-s- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -s-e-r-v-e-r-,- -a-n-d- -O-l-l-a-m-a- -s-u-p-p-l-i-e-s- -t-h-e- -l-o-c-a-l- -l-a-n-g-u-a-g-e- -m-o-d-e-l-.- -D-o-c-k-e-r- -i-s- -u-s-e-d- -t-o- -p-a-c-k-a-g-e- -t-h-e- -e-n-t-i-r-e- -s-y-s-t-e-m- -i-n-t-o- -a- -c-o-n-s-i-s-t-e-n-t- -r-u-n-t-i-m-e- -e-n-v-i-r-o-n-m-e-n-t-.--
--
-K-e-y- -c-o-n-c-e-p-t-s- -e-x-p-l-o-r-e-d- -i-n-c-l-u-d-e- -c-o-n-t-a-i-n-e-r-i-z-a-t-i-o-n-,- -R-e-t-r-i-e-v-a-l---A-u-g-m-e-n-t-e-d- -G-e-n-e-r-a-t-i-o-n- -(-R-A-G-)-,- -v-e-c-t-o-r- -d-a-t-a-b-a-s-e-s-,- -A-I- -m-o-d-e-l- -i-n-t-e-g-r-a-t-i-o-n-,- -A-P-I- -d-e-v-e-l-o-p-m-e-n-t-,- -a-n-d- -D-o-c-k-e-r-f-i-l-e- -c-r-e-a-t-i-o-n-.--
--
-
--
-T-h-i-s- -p-r-o-j-e-c-t- -t-o-o-k- -a-p-p-r-o-x-i-m-a-t-e-l-y- -9-0- -m-i-n-u-t-e-s- -t-o- -c-o-m-p-l-e-t-e-.- -T-h-e- -p-r-i-m-a-r-y- -c-h-a-l-l-e-n-g-e- -w-a-s- -i-n-t-e-g-r-a-t-i-n-g- -t-h-e- -O-l-l-a-m-a- -l-a-n-g-u-a-g-e- -m-o-d-e-l- -i-n-t-o- -t-h-e- -c-o-n-t-a-i-n-e-r-i-z-e-d- -e-n-v-i-r-o-n-m-e-n-t- -a-n-d- -e-n-s-u-r-i-n-g- -i-t- -f-u-n-c-t-i-o-n-e-d- -c-o-r-r-e-c-t-l-y- -a-l-o-n-g-s-i-d-e- -t-h-e- -r-e-t-r-i-e-v-a-l- -c-o-m-p-o-n-e-n-t-s-.--
--
-T-h-e- -m-o-s-t- -r-e-w-a-r-d-i-n-g- -o-u-t-c-o-m-e- -w-a-s- -s-u-c-c-e-s-s-f-u-l-l-y- -r-u-n-n-i-n-g- -t-h-e- -R-A-G- -A-P-I- -i-n-s-i-d-e- -a- -D-o-c-k-e-r- -c-o-n-t-a-i-n-e-r- -w-i-t-h- -b-e-h-a-v-i-o-r- -i-d-e-n-t-i-c-a-l- -t-o- -t-h-e- -l-o-c-a-l- -s-e-t-u-p-.- -T-h-i-s- -c-o-n-f-i-r-m-e-d- -t-h-a-t- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -w-a-s- -f-u-l-l-y- -p-o-r-t-a-b-l-e- -a-n-d- -c-o-n-s-i-s-t-e-n-t-l-y- -d-e-p-l-o-y-a-b-l-e-.--
--
-
--
-I- -c-o-m-p-l-e-t-e-d- -t-h-i-s- -p-r-o-j-e-c-t- -t-o- -s-t-r-e-n-g-t-h-e-n- -m-y- -D-e-v-O-p-s- -s-k-i-l-l- -s-e-t- -b-y- -l-e-a-r-n-i-n-g- -h-o-w- -t-o- -c-o-n-t-a-i-n-e-r-i-z-e- -A-I---d-r-i-v-e-n- -a-p-p-l-i-c-a-t-i-o-n-s-.- -C-o-n-t-a-i-n-e-r-i-z-a-t-i-o-n- -i-s- -a- -c-r-i-t-i-c-a-l- -s-t-e-p- -i-n- -m-o-v-i-n-g- -f-r-o-m- -l-o-c-a-l- -d-e-v-e-l-o-p-m-e-n-t- -t-o- -r-e-l-i-a-b-l-e- -d-e-p-l-o-y-m-e-n-t-.--
--
-T-h-i-s- -p-r-o-j-e-c-t- -a-l-s-o- -r-e-i-n-f-o-r-c-e-d- -h-o-w- -A-I- -s-y-s-t-e-m-s- -a-r-e- -p-a-c-k-a-g-e-d- -a-n-d- -d-e-l-i-v-e-r-e-d- -i-n- -r-e-a-l- -e-n-v-i-r-o-n-m-e-n-t-s-,- -p-r-o-v-i-d-i-n-g- -h-a-n-d-s---o-n- -e-x-p-e-r-i-e-n-c-e- -w-i-t-h- -D-o-c-k-e-r- -a-l-o-n-g-s-i-d-e- -F-a-s-t-A-P-I-,- -C-h-r-o-m-a-,- -U-v-i-c-o-r-n-,- -a-n-d- -O-l-l-a-m-a-.--
--
------- -T-h-i-s- -p-r-o-j-e-c-t- -d-e-p-l-o-y-s- -a- -R-e-t-r-i-e-v-a-l---A-u-g-m-e-n-t-e-d- -G-e-n-e-r-a-t-i-o-n- -(-R-A-G-)- -A-P-I- -t-o- -K-u-b-e-r-n-e-t-e-s- -t-o- -d-e-m-o-n-s-t-r-a-t-e- -h-o-w- -c-o-n-t-a-i-n-e-r-i-z-e-d- -A-I- -s-e-r-v-i-c-e-s- -a-r-e- -o-r-c-h-e-s-t-r-a-t-e-d-,- -m-a-n-a-g-e-d-,- -a-n-d- -k-e-p-t- -a-v-a-i-l-a-b-l-e- -i-n- -a- -p-r-o-d-u-c-t-i-o-n---s-t-y-l-e- -e-n-v-i-r-o-n-m-e-n-t-.--
--
-T-h-e- -g-o-a-l- -i-s- -t-o- -m-o-v-e- -b-e-y-o-n-d- -s-i-n-g-l-e---h-o-s-t- -c-o-n-t-a-i-n-e-r- -e-x-e-c-u-t-i-o-n- -a-n-d- -a-p-p-l-y- -K-u-b-e-r-n-e-t-e-s- -p-r-i-m-i-t-i-v-e-s- -t-o- -m-a-n-a-g-e- -a-p-p-l-i-c-a-t-i-o-n- -l-i-f-e-c-y-c-l-e-,- -a-v-a-i-l-a-b-i-l-i-t-y-,- -a-n-d- -a-c-c-e-s-s-.- -T-h-i-s- -p-r-o-j-e-c-t- -f-o-c-u-s-e-s- -o-n- -u-n-d-e-r-s-t-a-n-d-i-n-g- -h-o-w- -K-u-b-e-r-n-e-t-e-s- -a-b-s-t-r-a-c-t-s- -i-n-f-r-a-s-t-r-u-c-t-u-r-e- -c-o-m-p-l-e-x-i-t-y- -w-h-i-l-e- -p-r-o-v-i-d-i-n-g- -r-e-l-i-a-b-i-l-i-t-y- -g-u-a-r-a-n-t-e-e-s- -f-o-r- -A-I---d-r-i-v-e-n- -s-e-r-v-i-c-e-s-.--
--
-
--
-T-h-e- -t-o-o-l-s- -u-s-e-d- -i-n- -t-h-i-s- -p-r-o-j-e-c-t- -a-r-e- -M-i-n-i-k-u-b-e-,- -k-u-b-e-c-t-l-,- -D-o-c-k-e-r-,- -a-n-d- -F-a-s-t-A-P-I-.--
--
-D-o-c-k-e-r- -i-s- -u-s-e-d- -t-o- -p-a-c-k-a-g-e- -t-h-e- -R-A-G- -A-P-I- -i-n-t-o- -a- -c-o-n-t-a-i-n-e-r- -i-m-a-g-e-.- -M-i-n-i-k-u-b-e- -p-r-o-v-i-d-e-s- -a- -l-o-c-a-l- -K-u-b-e-r-n-e-t-e-s- -c-l-u-s-t-e-r- -f-o-r- -e-x-p-e-r-i-m-e-n-t-a-t-i-o-n- -a-n-d- -v-a-l-i-d-a-t-i-o-n-.- -k-u-b-e-c-t-l- -i-s- -u-s-e-d- -t-o- -i-n-t-e-r-a-c-t- -w-i-t-h- -t-h-e- -c-l-u-s-t-e-r- -a-n-d- -m-a-n-a-g-e- -r-e-s-o-u-r-c-e-s-.- -F-a-s-t-A-P-I- -s-e-r-v-e-s- -a-s- -t-h-e- -a-p-p-l-i-c-a-t-i-o-n- -f-r-a-m-e-w-o-r-k- -f-o-r- -t-h-e- -R-A-G- -A-P-I-.--
--
-K-e-y- -c-o-n-c-e-p-t-s- -e-x-p-l-o-r-e-d- -i-n-c-l-u-d-e- -K-u-b-e-r-n-e-t-e-s- -o-r-c-h-e-s-t-r-a-t-i-o-n-,- -c-o-n-t-a-i-n-e-r- -l-i-f-e-c-y-c-l-e- -m-a-n-a-g-e-m-e-n-t-,- -d-e-p-l-o-y-m-e-n-t-s-,- -s-e-r-v-i-c-e-s-,- -s-e-l-f---h-e-a-l-i-n-g- -b-e-h-a-v-i-o-r-,- -a-n-d- -a-p-p-l-y-i-n-g- -R-A-G- -s-y-s-t-e-m-s- -i-n- -a-n- -o-r-c-h-e-s-t-r-a-t-e-d- -e-n-v-i-r-o-n-m-e-n-t-.--
--
-
--
-T-h-i-s- -p-r-o-j-e-c-t- -t-o-o-k- -a-p-p-r-o-x-i-m-a-t-e-l-y- -9-0- -m-i-n-u-t-e-s- -t-o- -c-o-m-p-l-e-t-e-.- -T-h-e- -m-o-s-t- -c-h-a-l-l-e-n-g-i-n-g- -a-s-p-e-c-t- -w-a-s- -u-n-d-e-r-s-t-a-n-d-i-n-g- -h-o-w- -K-u-b-e-r-n-e-t-e-s- -Y-A-M-L- -d-e-f-i-n-i-t-i-o-n-s- -t-r-a-n-s-l-a-t-e- -i-n-t-o- -r-u-n-n-i-n-g- -i-n-f-r-a-s-t-r-u-c-t-u-r-e-,- -p-a-r-t-i-c-u-l-a-r-l-y- -h-o-w- -D-e-p-l-o-y-m-e-n-t-s- -a-n-d- -S-e-r-v-i-c-e-s- -i-n-t-e-r-a-c-t-.--
--
-T-h-e- -m-o-s-t- -r-e-w-a-r-d-i-n-g- -o-u-t-c-o-m-e- -w-a-s- -o-b-s-e-r-v-i-n-g- -t-h-e- -R-A-G- -A-P-I- -r-u-n-n-i-n-g- -r-e-l-i-a-b-l-y- -i-n-s-i-d-e- -K-u-b-e-r-n-e-t-e-s-,- -r-e-s-p-o-n-d-i-n-g- -t-o- -r-e-q-u-e-s-t-s-,- -a-n-d- -a-u-t-o-m-a-t-i-c-a-l-l-y- -r-e-c-o-v-e-r-i-n-g- -f-r-o-m- -p-o-d- -f-a-i-l-u-r-e-s-.- -T-h-i-s- -d-e-m-o-n-s-t-r-a-t-e-d- -K-u-b-e-r-n-e-t-e-s-'- -v-a-l-u-e- -a-s- -a-n- -o-r-c-h-e-s-t-r-a-t-i-o-n- -p-l-a-t-f-o-r-m- -f-o-r- -A-I- -w-o-r-k-l-o-a-d-s-.--
--
-
--
-I- -c-o-m-p-l-e-t-e-d- -t-h-i-s- -p-r-o-j-e-c-t- -t-o- -g-a-i-n- -h-a-n-d-s---o-n- -e-x-p-e-r-i-e-n-c-e- -w-i-t-h- -K-u-b-e-r-n-e-t-e-s- -a-n-d- -u-n-d-e-r-s-t-a-n-d- -h-o-w- -i-t- -s-i-m-p-l-i-f-i-e-s- -t-h-e- -d-e-p-l-o-y-m-e-n-t- -a-n-d- -m-a-n-a-g-e-m-e-n-t- -o-f- -c-o-n-t-a-i-n-e-r-i-z-e-d- -A-I- -a-p-p-l-i-c-a-t-i-o-n-s-.--
--
-T-h-e- -k-e-y- -t-a-k-e-a-w-a-y- -i-s- -t-h-e- -p-r-a-c-t-i-c-a-l- -u-s-e- -o-f- -d-e-c-l-a-r-a-t-i-v-e- -Y-A-M-L- -c-o-n-f-i-g-u-r-a-t-i-o-n- -t-o- -d-e-f-i-n-e- -d-e-s-i-r-e-d- -s-y-s-t-e-m- -s-t-a-t-e-,- -a-l-l-o-w-i-n-g- -K-u-b-e-r-n-e-t-e-s- -t-o- -m-a-n-a-g-e- -a-v-a-i-l-a-b-i-l-i-t-y-,- -r-e-c-o-v-e-r-y-,- -a-n-d- -r-o-u-t-i-n-g- -w-i-t-h-o-u-t- -m-a-n-u-a-l- -i-n-t-e-r-v-e-n-t-i-o-n-.--
--
-------

## Architecture

Per-build architecture diagrams. Each link opens a focused Mermaid diagram for that specific build:

- **[Build a RAG API with FastAPI](./diagrams/01-ai-devops-api.md)**, RAG · API · FastAPI · Retrieval-Augmented
- **[Containerize a RAG API with Docker](./diagrams/02-ai-devops-docker.md)**, RAG · API · Docker · Retrieval-Augmented
- **[Deploy a RAG API to Kubernetes](./diagrams/03-ai-devops-kubernetes.md)**, RAG · API · Retrieval-Augmented · AI
- **[Automate Testing with GitHub Actions](./diagrams/04-ai-devops-githubactions.md)**, GitHub · CI · CD · Retrieval-Augmented

## Implementation

**Build sequence.** Ordered builds, each step is a complete system the next builds on:

1. **[Build a RAG API with FastAPI](./documents/01-ai-devops-api.md)**, RAG · API · FastAPI · Retrieval-Augmented
2. **[Containerize a RAG API with Docker](./documents/02-ai-devops-docker.md)**, RAG · API · Docker · Retrieval-Augmented
3. **[Deploy a RAG API to Kubernetes](./documents/03-ai-devops-kubernetes.md)**, RAG · API · Retrieval-Augmented · AI
4. **[Automate Testing with GitHub Actions](./documents/04-ai-devops-githubactions.md)**, GitHub · CI · CD · Retrieval-Augmented

## Validation

Build outcomes verified end-to-end. Each is captured with screenshots, configuration, and observable behavior in [`documents/`](./documents/):

- ✅ Build a RAG API with FastAPI
- ✅ Containerize a RAG API with Docker
- ✅ Deploy a RAG API to Kubernetes
- ✅ Automate Testing with GitHub Actions
