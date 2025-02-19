# My-Values
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Blog</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 p-6">
    <div class="max-w-2xl mx-auto bg-white p-6 rounded-xl shadow-md">
        <h1 class="text-2xl font-bold mb-4">My Video Blog</h1>
        <form id="uploadForm" class="mb-4">
            <input type="file" id="videoInput" accept="video/*" class="block w-full mb-2" required>
            <input type="text" id="descInput" placeholder="Enter description" class="block w-full p-2 border rounded mb-2" required>
            <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">Upload</button>
        </form>
        <div id="videoList"></div>
    </div>
    
    <script>
        document.getElementById('uploadForm').addEventListener('submit', function(event) {
            event.preventDefault();
            
            let videoFile = document.getElementById('videoInput').files[0];
            let description = document.getElementById('descInput').value;
            
            if (videoFile && description) {
                let videoURL = URL.createObjectURL(videoFile);
                let videoContainer = document.createElement('div');
                videoContainer.classList.add('mb-4', 'p-4', 'bg-gray-200', 'rounded');
                
                videoContainer.innerHTML = `
                    <video controls class="w-full rounded">
                        <source src="${videoURL}" type="${videoFile.type}">
                        Your browser does not support the video tag.
                    </video>
                    <p class="mt-2 text-gray-700">${description}</p>
                `;
                
                document.getElementById('videoList').prepend(videoContainer);
                document.getElementById('uploadForm').reset();
            }
        });
    </script>
</body>
</html>
