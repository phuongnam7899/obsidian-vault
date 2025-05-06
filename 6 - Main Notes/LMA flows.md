cd /opt
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
# Azure
- Login https://portal.azure.com/
## VM
### General actions
- Connect -> Bastion:
	- Select protocol RFP
	- Enter Port
	- Auth type: VM Password
	- Username: psamsysadmin
	- Password: $trongP@ssw0rd01
- Connect to DB: [[Account]]
- Reset credential (to download build file for deployment): `az login --tenant bc1b92b9-5dc9-49be-995b-c97eb515a1d3`
### fleetadm01a
- Use to:
	- Postman (to send job to LMA/TMA PROD)
	- DB PROD
	- View LMA/TMA PROD services logs
	- Deploy LMA/TMA PROD

#### Deploy services
- Build jar file
	- Start Jenkin in .43.23 if need:
		- Window -> Search "Services"
		- Find Jenkins -> Right CLick -> Properties -> Log On -> Local System account -> Apply -> Start
		- Right CLick -> Properties -> Log On -> This account -> Enter password -> Apply -> Restart service
	- Login to Jenkin:
		- URL: [http://10.1.43.23:8181/](http://10.1.43.23:8181/)  
		- Account: admin/admin
	- Click "Play" icon (to build jar file)
- Run deployment script in `deploy-backend/LMA/` or  `deploy-backend/TMA/` (each environment has a file)


> For PMA: run `mvn clean package -DskipTests=true` to build jar file inlcoal


### fleetnprdseaamq1a
- Use to 
	- host activeMQ
	- host P360 SIT/FAT

### fleetnprdadm01a
- Account: psamadmin / P@ssw0rd
- Use to:
	- Postman (to send job to LMA/TMA SIT/UAT)
	- DB SIT/UAT
	- View LMA/TMA SIT/UAT services logs
	- Deploy LMA/TMA SIT/UAT
## Services
- View logs:
	- Login to azure portal in VM `fleetadm01a`
	- Go to `App Services` -> Select service to view logs
	- SSH to server
	- View latest 1000 line of logs: `tail -n 1000 ./LogFiles/Applications/[...].log`



- Restart P360:


# Gateway management
![[Pasted image 20250421090657.png]]
## Custom request/response headers
![[Pasted image 20250421090754.png]]

# FE Code
- Routing: `src\app\epics\layout\layout-routing.module.ts`
	- `path`: route in browser
	- `component`: which component to be render
	- `canActivate`: define guard to handle logic before access to a path
	- `data`: custom data passes when come to page
		- `title`: page title shown on screen
- Screens: each screen stored in a folder inside `src/app/epics`
- Component structure:
	- HTML file:
		- HTML file can use properties declared in the TS file
		- To render based on list: `*ngFor`
	- SCSS file
	- TS file:
		- `@Component` decorator: define metadata:
			- Selector: used to use that component in other component (use like a tag name)
			- Template file: link to HTML file
			- Style files
		- Class properties
		- Class methods