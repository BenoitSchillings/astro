<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NGC Galaxy Finder</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .loader {
            border-top-color: #3498db;
            -webkit-animation: spin 1s linear infinite;
            animation: spin 1s linear infinite;
        }
        @-webkit-keyframes spin {
            0% { -webkit-transform: rotate(0deg); }
            100% { -webkit-transform: rotate(360deg); }
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="bg-gray-900 text-gray-100 p-4 sm:p-6 lg:p-8">

    <div class="max-w-7xl mx-auto">
        <header class="text-center mb-8">
            <h1 class="text-3xl sm:text-4xl font-bold text-white">NGC Galaxy Finder</h1>
            <p class="text-gray-400 mt-2">Find large galaxies visible from your location.</p>
        </header>

        <!-- Main controls section -->
        <div class="bg-gray-800 p-6 rounded-2xl shadow-lg mb-8">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-6">
                <!-- Location Inputs -->
                <div>
                    <label for="latitude" class="block text-sm font-medium text-gray-300 mb-1">Latitude</label>
                    <input type="number" id="latitude" value="37.37" class="w-full bg-gray-700 border-gray-600 text-white rounded-md p-2 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div>
                    <label for="longitude" class="block text-sm font-medium text-gray-300 mb-1">Longitude</label>
                    <input type="number" id="longitude" value="-122.14" class="w-full bg-gray-700 border-gray-600 text-white rounded-md p-2 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                </div>

                <!-- Date and Time Inputs -->
                <div>
                    <label for="date" class="block text-sm font-medium text-gray-300 mb-1">Date</label>
                    <input type="date" id="date" value="2025-06-21" class="w-full bg-gray-700 border-gray-600 text-white rounded-md p-2 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div>
                    <label for="time" class="block text-sm font-medium text-gray-300 mb-1">Time</label>
                    <input type="time" id="time" value="16:20" class="w-full bg-gray-700 border-gray-600 text-white rounded-md p-2 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                </div>

                <!-- Action Button -->
                <div class="lg:self-end">
                    <button id="find-galaxies-btn" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md transition duration-300 h-full flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" /></svg>
                        Find Galaxies
                    </button>
                </div>
            </div>
        </div>

        <!-- Results Section -->
        <div id="results-container" class="bg-gray-800 p-4 sm:p-6 rounded-2xl shadow-lg">
            <div id="status-message" class="text-center text-gray-400">
                <p>Adjust the parameters above and click "Find Galaxies" to begin.</p>
            </div>
            <div id="loader" class="hidden loader ease-linear rounded-full border-4 border-t-4 border-gray-200 h-12 w-12 mx-auto my-4"></div>
            <div class="overflow-x-auto">
                <table id="results-table" class="min-w-full text-left text-sm sm:text-base hidden">
                    <thead class="bg-gray-700">
                        <tr>
                            <th class="px-4 py-3 font-medium text-gray-200">NGC</th>
                            <th class="px-4 py-3 font-medium text-gray-200">Type</th>
                            <th class="px-4 py-3 font-medium text-gray-200">Constellation</th>
                            <th class="px-4 py-3 font-medium text-gray-200">RA</th>
                            <th class="px-4 py-3 font-medium text-gray-200">Dec</th>
                            <th class="px-4 py-3 font-medium text-gray-200">Size (arcmin)</th>
                            <th class="px-4 py-3 font-medium text-gray-200">Altitude (&deg;)</th>
                        </tr>
                    </thead>
                    <tbody id="results-body" class="divide-y divide-gray-700">
                        <!-- Results will be injected here by JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // --- DOM Elements ---
            const findBtn = document.getElementById('find-galaxies-btn');
            const resultsTable = document.getElementById('results-table');
            const resultsBody = document.getElementById('results-body');
            const statusMessage = document.getElementById('status-message');
            const loader = document.getElementById('loader');

            let ngcData = [];

            // --- Astronomical Calculation Functions ---

            /**
             * Converts RA string (HH MM SS.S) to decimal degrees.
             */
            const raToDegrees = (raStr) => {
                if (!raStr) return 0;
                const parts = raStr.split(' ').map(parseFloat);
                const hours = parts[0] || 0;
                const minutes = parts[1] || 0;
                const seconds = parts[2] || 0;
                return (hours * 15) + (minutes / 4) + (seconds / 240);
            };

            /**
             * Converts Dec string (+/-DD MM SS) to decimal degrees.
             */
            const decToDegrees = (decStr) => {
                if (!decStr) return 0;
                const sign = decStr.startsWith('-') ? -1 : 1;
                const parts = decStr.replace(/[-+]/, '').split(' ').map(parseFloat);
                const degrees = parts[0] || 0;
                const minutes = parts[1] || 0;
                const seconds = parts[2] || 0;
                return sign * (degrees + (minutes / 60) + (seconds / 3600));
            };
            
            const toRadians = (degrees) => degrees * (Math.PI / 180);

            const calculateAltitude = (raDeg, decDeg, lat, lon, dateObj) => {
                const utcMillis = dateObj.getTime();
                const julianDate = (utcMillis / 86400000) + 2440587.5;
                const T = (julianDate - 2451545.0) / 36525;
                let gmst = 280.46061837 + 360.98564736629 * (julianDate - 2451545.0) + 0.000387933 * T * T - (T * T * T) / 38710000;
                gmst %= 360; if (gmst < 0) gmst += 360;
                let lst = gmst + lon;
                lst %= 360; if (lst < 0) lst += 360;
                let ha = lst - raDeg;
                if (ha < 0) ha += 360;
                const latRad = toRadians(lat);
                const decRad = toRadians(decDeg);
                const haRad = toRadians(ha);
                const sinAlt = Math.sin(decRad) * Math.sin(latRad) + Math.cos(decRad) * Math.cos(latRad) * Math.cos(haRad);
                const altRad = Math.asin(sinAlt);
                return altRad * (180 / Math.PI);
            };

            // --- Main Application Logic ---

            const findAndDisplayGalaxies = () => {
                loader.classList.remove('hidden');
                statusMessage.classList.add('hidden');
                resultsTable.classList.add('hidden');
                resultsBody.innerHTML = '';

                const lat = parseFloat(document.getElementById('latitude').value);
                const lon = parseFloat(document.getElementById('longitude').value);
                const dateStr = document.getElementById('date').value;
                const timeStr = document.getElementById('time').value;

                if (isNaN(lat) || isNaN(lon) || !dateStr || !timeStr) {
                    statusMessage.textContent = 'Please fill in all location, date, and time fields correctly.';
                    statusMessage.classList.remove('hidden');
                    loader.classList.add('hidden');
                    return;
                }
                
                const observationDate = new Date(`${dateStr}T${timeStr}`);
                const foundGalaxies = [];
                
                for (const obj of ngcData) {
                    const raDeg = raToDegrees(obj.RA);
                    const decDeg = decToDegrees(obj.Dec);
                    
                    const altitude = calculateAltitude(raDeg, decDeg, lat, lon, observationDate);

                    if (altitude > 40) {
                        foundGalaxies.push({
                            ...obj,
                            altitude: altitude.toFixed(2),
                        });
                    }
                }
                
                loader.classList.add('hidden');
                displayResults(foundGalaxies);
            };

            const displayResults = (galaxies) => {
                if (galaxies.length > 0) {
                    galaxies.forEach(galaxy => {
                        const row = document.createElement('tr');
                        row.className = 'hover:bg-gray-700/50 transition-colors';
                        
                        row.innerHTML = `
                            <td class="px-4 py-3">${galaxy.NGC || 'N/A'}</td>
                            <td class="px-4 py-3">${galaxy.Type || 'N/A'}</td>
                            <td class="px-4 py-3">${galaxy.Const || 'N/A'}</td>
                            <td class="px-4 py-3">${galaxy.RA || 'N/A'}</td>
                            <td class="px-4 py-3">${galaxy.Dec || 'N/A'}</td>
                            <td class="px-4 py-3">${galaxy.MajAx || 'N/A'}</td>
                            <td class="px-4 py-3 font-semibold text-cyan-400">${galaxy.altitude}</td>
                        `;
                        resultsBody.appendChild(row);
                    });
                    resultsTable.classList.remove('hidden');
                } else {
                    statusMessage.textContent = `No galaxies found matching your criteria. Try a different time or location.`;
                    statusMessage.classList.remove('hidden');
                }
            };
            
            /**
             * Initializes the application by fetching the NGC data from the VizieR service.
             */
            const initialize = async () => {
                statusMessage.textContent = 'Loading galaxy catalog from VizieR...';
                loader.classList.remove('hidden');
                
                // FIX: The direct request to VizieR was being blocked by CORS.
                // The URL is now routed through a CORS proxy to resolve the "Failed to fetch" error.
                const originalVizierURL = 'https://vizier.u-strasbg.fr/viz-bin/asu-tsv?-source=VII/280/OpenNGC&-out.all=&MajAx=>=2';
                const proxyURL = 'https://api.allorigins.win/raw?url=';
                const vizierURL = proxyURL + encodeURIComponent(originalVizierURL);

                try {
                    const response = await fetch(vizierURL);
                    if (!response.ok) {
                        throw new Error(`HTTP error! status: ${response.status}`);
                    }
                    const tsvData = await response.text();
                    
                    // Parse the TSV data from VizieR
                    const lines = tsvData.split('\n');
                    const dataLines = lines.filter(line => !line.startsWith('#') && line.trim() !== '');
                    
                    if (dataLines.length < 2) {
                        throw new Error('No data returned from VizieR.');
                    }

                    const headers = dataLines[0].split('\t');
                    const dataRows = dataLines.slice(1);
                    
                    const parsedData = dataRows.map(rowStr => {
                        const row = rowStr.split('\t');
                        const obj = {};
                        headers.forEach((header, index) => {
                            obj[header.trim()] = row[index];
                        });
                        return obj;
                    });

                    // Filter for galaxies and map properties to the format our app expects
                    ngcData = parsedData
                        .filter(obj => obj.Type && obj.Type.trim().toLowerCase() === 'galaxy')
                        .map(obj => ({
                            NGC: obj.Name,
                            Type: obj.Type,
                            Const: obj.Const,
                            RA: obj.RA,
                            Dec: obj.DE, // VizieR uses DE for Declination
                            MajAx: obj.MajAx
                        }));

                    statusMessage.textContent = `Catalog ready (${ngcData.length} galaxies). Set your parameters and find galaxies.`;
                    findBtn.disabled = false;

                } catch (error) {
                    console.error('Failed to load NGC catalog from VizieR:', error);
                    statusMessage.innerHTML = `Error: Could not load the NGC catalog from VizieR. <br> The service may be temporarily unavailable. Please try again later.`;
                } finally {
                    loader.classList.add('hidden');
                }
            };

            // --- Event Listeners ---
            findBtn.addEventListener('click', findAndDisplayGalaxies);
            findBtn.disabled = true;

            initialize();
        });
    </script>
</body>
</html>
