# UAV-Data-Collection-from-Sensor-Nodes
Wireless Networks concept 
# 🚁 UAV-Based Wireless Sensor Network Data Collection - ns-3 Simulation

## 📋 Project Overview

This project simulates a **Wireless Sensor Network (WSN)** where a **UAV (Unmanned Aerial Vehicle)** collects data from multiple static ground sensor nodes using ns-3 network simulator. The UAV follows a predefined lawnmower flight pattern and collects data when within range of sensors.

![Project Visualization](https://via.placeholder.com/800x400?text=UAV+WSN+Collection+Simulation)

## ✨ Features

- **UAV Mobility**: Waypoint-based lawnmower flight pattern at 50m altitude
- **Static Sensor Nodes**: 10+ ground sensors placed in grid pattern
- **WiFi Communication**: 802.11g ad-hoc mode for UAV-sensor communication
- **Data Collection**: Automatic packet transmission when UAV is in range
- **Visualization**: NetAnim animation support for visual debugging
- **Performance Metrics**: Tracks packets collected, bytes transferred, collection efficiency
- **Configurable Parameters**: Number of sensors, UAV speed, collection range, simulation time

## 🛠️ Requirements

- **ns-3.43** or later
- **NetAnim** (for visualization, optional)
- **C++ compiler** with C++17 support
- **Python3** (for test scripts)

## 📦 Installation

### 1. Clone/Download the Project

```bash
# Navigate to ns-3 scratch directory
cd ~/ns-allinone-3.43/ns-3.43/scratch/

# Create the project file
nano wsn-uav-collection.cc
```

### 2. Copy the Source Code

Copy the complete source code from [SOURCE_CODE_LINK] or paste the code provided in the project documentation.

### 3. Build the Project

```bash
cd ~/ns-allinone-3.43/ns-3.43
./ns3 build
```

### 4. Install NetAnim (Optional - for visualization)

```bash
cd ~
sudo apt install qt5-default
wget https://www.nsnam.org/releases/netanim-3.108.tar.bz2
tar -xjf netanim-3.108.tar.bz2
cd netanim-3.108
qmake NetAnim.pro
make
```

## 🚀 Usage

### Basic Run

```bash
cd ~/ns-allinone-3.43/ns-3.43
./ns3 run scratch/wsn-uav-collection
```

### Custom Parameters

```bash
# Run with 20 sensors, UAV speed 10 m/s, for 200 seconds
./ns3 run "scratch/wsn-uav-collection --numSensors=20 --uavSpeed=10 --time=200"

# Run with 5 sensors, collection range 100m
./ns3 run "scratch/wsn-uav-collection --numSensors=5 --range=100"
```

### Available Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| `--numSensors` | Number of ground sensor nodes | 10 |
| `--time` | Total simulation time (seconds) | 100 |
| `--uavSpeed` | UAV speed (m/s) | 5.0 |
| `--range` | Data collection range (meters) | 50.0 |
| `--animate` | Enable/disable NetAnim animation | true |

### Visualization with NetAnim

```bash
# Run simulation to generate animation file
./ns3 run scratch/wsn-uav-collection

# Open NetAnim
cd ~/netanim-3.108
./NetAnim

# In NetAnim GUI: File → Open → Select ~/ns-allinone-3.43/ns-3.43/wsn-uav-collection.xml
```

## 📊 Output and Results

### Console Output Example

```
🚀 Starting UAV WSN Collection Simulation
📊 Configuration: 10 sensors, 100s duration, UAV speed 5 m/s
▶️ Starting simulation...
🚁 UAV received packet #1 (64 bytes) at time 5.23s
🚁 UAV received packet #2 (64 bytes) at time 7.89s
...
✅ Simulation Complete!
📊 Summary:
   - Total packets collected by UAV: 42
   - Total bytes collected: 2688
   - Collection efficiency: 84%
```

### Generated Files

| File | Description |
|------|-------------|
| `wsn-uav-collection.xml` | NetAnim animation file |
| `wsn-uav-*.pcap` | Packet capture files for each node |
| `flowmonitor.xml` | Flow monitor statistics (if enabled) |

## 🔧 Project Structure

```
scratch/
└── wsn-uav-collection.cc      # Main simulation script

ns-3.43/
├── build/                      # Compiled binaries
├── wsn-uav-collection.xml      # Animation output
└── *.pcap                      # Packet traces
```

## 📈 Key Simulation Components

### 1. **Node Configuration**
- **UAV Node**: Mobile collector (red in animation)
- **Sensor Nodes**: Static ground sensors (green in animation)

### 2. **Mobility Models**
- **UAV**: `WaypointMobilityModel` with lawnmower pattern
- **Sensors**: `ConstantPositionMobilityModel` in grid layout

### 3. **Communication**
- **WiFi Standard**: 802.11g
- **Mode**: Ad-hoc (direct node-to-node)
- **Application**: UDP client-server for data transfer

### 4. **Data Collection Logic**
- Sensors periodically send UDP packets to UAV
- Packets only received when UAV is within range
- Collection efficiency calculated based on successful transmissions

## 🧪 Experiment Ideas

### 1. **Vary UAV Speed**
```bash
for speed in 2 5 10 15 20; do
    ./ns3 run "scratch/wsn-uav-collection --uavSpeed=$speed --numSensors=10"
done
```

### 2. **Change Sensor Density**
```bash
for sensors in 5 10 20 50; do
    ./ns3 run "scratch/wsn-uav-collection --numSensors=$sensors"
done
```

### 3. **Test Different Collection Ranges**
```bash
for range in 30 50 75 100; do
    ./ns3 run "scratch/wsn-uav-collection --range=$range"
done
```

## 🐛 Troubleshooting

| Problem | Solution |
|---------|----------|
| **Build fails** | Run `./ns3 clean` then `./ns3 configure --enable-examples --enable-tests` |
| **No packets received** | Check collection range; ensure UAV path covers sensor area |
| **NetAnim not showing movement** | Verify `--animate=true` parameter; check XML file exists |
| **Slow simulation** | Reduce number of sensors or simulation time |
| **Memory errors** | Decrease simulation scale; close other applications |

## 📚 References

- [ns-3 Tutorial](https://www.nsnam.org/docs/tutorial/html/)
- [ns-3 Mobility Models](https://www.nsnam.org/docs/models/html/mobility.html)
- [WiFi Module Documentation](https://www.nsnam.org/docs/models/html/wifi.html)
- [NetAnim Documentation](https://www.nsnam.org/wiki/NetAnim)

## 🤝 Contributing

Feel free to extend this project with:
- Multiple UAVs coordination
- Dynamic path planning based on data urgency
- Energy consumption models for sensors
- Different MAC protocols
- Realistic channel models with obstacles
- Machine learning for optimal UAV trajectory

## 📝 License

This project is for educational purposes. Use and modify freely for academic work.

## 👨‍💻 Author

Areeba Yasir



---

**Happy Simulating!** 🚁📡
