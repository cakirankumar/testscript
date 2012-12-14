testscript
==========
#!/bin/bash
#
#
while :
do
echo " M A I N - M E N U"
echo "1. Change Passwd"
echo "2. Disk Space"
echo "3. ssh to Box"
echo "4. Show all services running"
echo "5. Show all ports openend"
echo "6. Show all java apps running"
echo "7. Facility to kill app"
echo "8. Exit"
echo -n "Please enter option [1 - 8]"
read opt
case $opt in
1) echo "*Change passwd*";
passwd;;
2) echo "*Disk Space*";
df -h | more;;
3) echo "ssh to box";
echo "Enter box name";
read boxname
echo "Enter username";
read username
ssh $username@$boxname;;
4) echo "*Running Services*";
service --status-all | more;;
5) echo "*List of opened ports*";
netstat -an | egrep 'Proto|LISTEN';;
6) echo "*List of java processes running*";
ps -xauww | grep java | grep www;;
7) echo "*Enter app name to be killed*";
read appname
killall `ps h -o pid -C $appname`;;
8) echo "Bye $USER";
exit 1;;
*) echo "$opt is an invaild option. Please select option between 1-8 only";
echo "Press [enter] key to continue. . .";
read enterKey;;
esac
done
