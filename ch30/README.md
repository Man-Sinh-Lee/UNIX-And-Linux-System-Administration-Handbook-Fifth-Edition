Chapter 30 on data center basics from the *UNIX and Linux System Administration Handbook, Fifth Edition*:

### 30.1 RACKS
Modern data centers prioritize organization and accessibility:
- **Raised Floors**: Used primarily for power feeds and air distribution, not for network cabling.
- **Rack Mounting**: Servers and equipment are stored in racks rather than on tables for maintainability.
- **Overhead Tracks**: These are used to route cables, promoting neatness and ease of maintenance.

### 30.2 POWER
Reliable power is critical, with strategies including:
- **Uninterruptible Power Supplies (UPSs)**: Provide short-term power during outages, bridging until generators start.
- **On-Site Generators**: Fuel options include diesel or natural gas, and they should have a 72-hour fuel reserve.
- **Redundant Power Feeds**: If possible, leverage multiple power sources from different grids.
- **Monitoring**: UPSs and generators should have interfaces for alerts and status reporting.

**Note**: For AC power, use the conversion \( kVA = \frac{kW}{0.85} \) to estimate requirements.

### 30.3 COOLING AND ENVIRONMENT
Maintaining proper temperature is essential for hardware longevity:
- **Temperature Range**: ASHRAE recommends server inlet temperatures of 64.4° to 80.6°F (18° to 27°C).
- **Cooling Strategy**: Utilize hot and cold aisles to optimize airflow. Cold aisles have perforated tiles for cool air, while hot aisles expel warm exhaust.
- **Humidity Control**: Keep humidity between 8% and 60% to avoid static electricity or condensation.

### 30.4 DATA CENTER RELIABILITY TIERS
The **Uptime Institute** classifies data centers using a four-tier system:
- **Tier I**: Basic site infrastructure.
- **Tier II**: Redundant components.
- **Tier III**: Concurrently maintainable infrastructure.
- **Tier IV**: Fault-tolerant with compartmentalization.

Tiers indicate reliability, with Tier IV boasting the highest availability and minimal downtime.

### 30.5 DATA CENTER SECURITY
Security focuses on protecting against natural and human threats:
- **Location**: Choose sites away from hazard-prone areas (e.g., flood zones, refineries).
- **Perimeter**: Use fences, security guards, and multifactor access systems.
- **Facility Access**: Control entry with badge systems and biometric verification.
- **Rack Access**: Secure shared racks with locked cages and video monitoring.

### 30.6 TOOLS
A sysadmin's toolkit should include:
- **Power Meters**: To measure energy consumption.
- **Infrared Thermometers**: For quick temperature checks (e.g., Fluke 62).
- **Remote Control Systems**: Manage servers that require regular reboots.

### 30.7 RECOMMENDED READING
- **ASHRAE Thermal Guidelines for Data Processing Environments (3rd edition)**
- ANSI/TIA/EIA 942: *Telecommunications Infrastructure Standard for Data Centers*