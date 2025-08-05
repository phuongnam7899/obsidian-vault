2025-05-19 08:26

Tags: [[TMA-LMA]]

---

# Download necessary libs
## 1. Create container folder
- Create container folder:
```sh
sudo mkdir -p /opt/psa
```
- Go to that folder:
```sh
cd /opt/psa
```

## 2. Download Java
- Downlaod JDK 17
```sh
wget https://download.oracle.com/java/17/archive/jdk-17.0.12_linux-x64_bin.tar.gz
```
- Unzip activemq:
```sh
tar -xvf jdk-17.0.12_linux-x64_bin.tar.gz
```
- (Optional) Delete tar file
```sh
rm jdk-17.0.12_linux-x64_bin.tar.gz
```
- (Optional) Change the folder name
```sh
mv ./jdk-17.0.12 ./jdk-17
```

## 3. Download ActiveMQ
- Download the activemq
```sh
wget https://archive.apache.org/dist/activemq/6.1.6/apache-activemq-6.1.6-bin.tar.gz
```
- Unzip activemq:
```sh
tar -xvf apache-activemq-6.1.6-bin.tar.gz
```
- (Optional) Delete tar file:
```sh
rm apache-activemq-6.1.6-bin.tar.gz
```

- (Optional) Change the folder name
```sh
mv ./apache-activemq-6.1.6 ./activemq
```

# Update the config
- Stop Firewall:
```sh
sudo systemctl disable firewalld
```

## Update bin config
- Go to bin folder:
```
cd /opt/psa/activemq/bin/
```
- Edit `setenv` file:
	- `vim setenv`
	- Commend out `JAVACMD` config
	- Remove commend `JAVA_HOME` and set the path to installed JDK: `JAVA_HOME="/opt/psa/jdk-17"`
	- Save & quit: `Ctrl + C` -> `:wq!`
## Update activemq config
- Go to config folder:
```sh
cd /opt/psa/activemq/conf
```
- Create original file `.orig` files (to backup):
```sh
cp activemq.xml activemq.xml.orig
cp jetty.xml jetty.xml.orig
cp users.properties users.properties.orig
cp groups.properties.orig groups.properties.orig
```
- Edit `activemq.xml `:
	- `vim activemq.xml `
	- Update purge rule for broker (add `schedulePeriodForDestinationPurge` prop ): `<broker xmlns="http://activemq.apache.org/schema/core" brokerName="localhost" schedulePeriodForDestinationPurge="10000" dataDirectory="${activemq.data}">`
	- Update `persistenceAdapter` (to sync data if has multiple AMQ instances): `<kahaDB directory="/mount/fleetprodamqshrddiskstrg/fleetprodamqfileshare/kahadb"/>`
	- Add new policy entries: 
		- `<policyEntry queue="lma.client.queue.>" gcInactiveDestinations="true" inactiveTimoutBeforeGC="30000"/>`
		- `<policyEntry queue="tma.client.queue.>" gcInactiveDestinations="true" inactiveTimoutBeforeGC="30000"/>`
	- Save and quit
- Edit `jetty.xml`:
	- `vim jetty.xml`
	- Update host prop: `<property name="host" value="0.0.0.0"/>`
# Manage the AMQ
- Enter bin folder: 
```sh
cd /opt/psa/activemq/bin
```
- Start:
```sh
sh activemq start
```
- Verify application is running (on `61613` ,`61614`  & `61616`):
```
netstat -tulnp | grep LISTEN
```
- Stop:
```sh
sh activemq stop
```
- View log:
```sh
cd /opt/psa/activemq/data
cat ./activemq.log
```
---
# References