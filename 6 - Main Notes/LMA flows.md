# Main BE code flow
![[LMA Code flows 2025-02-05 07.44.12.excalidraw]]

# Flow to receive new message
- 1. `MessageType.java`: add new message type, contains
	- `classType` (will define in step 2)
	- `dtoType` (will define in step 2)
- 2. `/messages/dto`:
	- Create `classType` to define the JSON mapping when received from MRES (Also need to create separate class to define message details if needed)
	- Create `dtoType` to...
- 3. Create new message service if need, then add it in the `JobMessageServiceFactory.java`
- 4. Create message builder class (like `BunkeringJobMessageBuilder`, `PilotJobMessageBuilder`)
# Dev/FAT environment management
- Login https://portal.azure.com/
- Select VM `fleetadm01a`
- Connect -> Bastion:
	- Select protocol RFP
	- Enter Port
	- Auth type: VM Password
	- Username: psamsysadmin
	- Password: $trongP@ssw0rd01
- Connect to DB: [[Account]]
- View logs:
	- Login to azure portal in virtual machine
	- SSH to server
	- View latest 1000 line of logs: `tail -n 1000 ./LogFiles/Applications/[...].log`
- Rebuild:
	- Build jar file
		- Login to Jenkin:
			- URL: [http://10.1.43.23:8181/](http://10.1.43.23:8181/)  
			- Account: admin/admin
		- Click "Play" icon (to build jar file)
	- Run deployment script in `deploy-backend/LMA/` or  `deploy-backend/TMA/` (each environment has a file)
# Manually Rebuild Dev Application