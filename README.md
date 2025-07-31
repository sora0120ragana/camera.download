<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>カメラ起動ページ</title>
</head>
<body>
  <h1>カメラ映像</h1>
  <video id="video" autoplay playsinline width="100%" height="auto" style="border: 1px solid #ccc;"></video>
  <p id="status"></p>

  <script>
    const video = document.getElementById('video');
    const status = document.getElementById('status');

    async function startCamera() {
      try {
        const stream = await navigator.mediaDevices.getUserMedia({ video: true });
        video.srcObject = stream;
        status.textContent = "カメラが起動しました。";
      } catch (err) {
        status.textContent = "カメラの使用が許可されませんでした。エラー：" + err.message;
      }
    }

    startCamera();
  </script>
</body>
</html>
