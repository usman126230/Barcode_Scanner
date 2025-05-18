<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Barcode Scanner - Online Sheet</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/lucide-react@0.10.0/dist/lucide-react.min.css" rel="stylesheet">
  <script src="https://unpkg.com/@zxing/library@latest"></script>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen">

  <div class="w-full max-w-lg p-4 bg-white shadow-lg">
    <h1 class="text-2xl font-semibold mb-4">Barcode Scanner</h1>

    <div class="space-y-4">
      <input 
        id="barcodeInput"
        type="text" 
        placeholder="Scan or enter barcode" 
        class="w-full p-2 border rounded mb-2" 
      />
      <button onclick="handleScan()" class="w-full bg-blue-500 text-white py-2 rounded">Scan</button>

      <div class="mt-4">
        <h2 class="text-lg font-medium mb-2">Scanned Items:</h2>
        <ul id="scannedItems" class="space-y-1">
        </ul>
      </div>
    </div>

    <div class="mt-6">
      <h2 class="text-lg font-medium mb-2">Camera Scanner:</h2>
      <video id="camera" class="w-full bg-gray-200 rounded mb-2"></video>
      <button onclick="startCamera()" class="w-full bg-green-500 text-white py-2 rounded">Start Camera</button>
    </div>
  </div>

  <script>
    const scannedItems = [];

    function handleScan() {
      const barcodeInput = document.getElementById('barcodeInput');
      const scannedItemsList = document.getElementById('scannedItems');
      const barcode = barcodeInput.value.trim();

      if (barcode) {
        scannedItems.push(barcode);
        const listItem = document.createElement('li');
        listItem.className = "flex items-center justify-between p-2 bg-gray-200 rounded";
        listItem.innerHTML = `<span>${barcode}</span><span class='text-green-500'>&#10003;</span>`;
        scannedItemsList.appendChild(listItem);
        barcodeInput.value = '';
      }
    }

    function startCamera() {
      const codeReader = new ZXing.BrowserBarcodeReader();
      const videoElement = document.getElementById('camera');

      codeReader.decodeOnceFromVideoDevice(undefined, videoElement)
        .then(result => {
          document.getElementById('barcodeInput').value = result.text;
          handleScan();
        })
        .catch(err => console.error(err));
    }
  </script>

</body>
</html>
