#!/bin/bash
Project URL: https://roadmap.sh/projects/server-stats

echo "=========================================================="
echo "          LAPORAN KESEHATAN SERVER - $(date)          "
echo "=========================================================="

echo ""

echo "[ CPU Usage ]"
top -bn1 | grep "Cpu(s)" | awk '{print "Total Penggunaan: "  $2 + $4 "%" }'
 
echo ""


echo "[ Memory Usage]"
free -h | grep "Mem" | awk '{print "Total: " $2 " / used: " $3 " / free: " $4}'

echo ""

echo "[Disk usage]"
df -h | grep "/$" | awk '{print "Total: " $2 "/ used: " $3 "/ free: "$4}'
 
echo ""



echo "[ Top 5 Processes by CPU  Usage ]"
ps -eo pid,ppid,cmd,%cpu --sort=-%cpu | head -n6

echo ""


echo "[ Top 5 Processes by Memory Usage ]"
ps -eo pid,ppid,cmd,%mem --sort=-%mem | head -n6

echo ""


echo "=========================================================="
echo "                Laporan Selesai - Mantap Bel!             "
echo "=========================================================="

