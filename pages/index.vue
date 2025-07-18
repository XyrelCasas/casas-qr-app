<template>
  <div>
    <div id="reader" style="width: 500px;"></div>
    <p>Scanned QR Code: {{ scannedResult }}</p>
  </div>
</template>

<script>
import { Html5Qrcode } from "html5-qrcode";

export default {
  data() {
    return {
      html5QrCode: null,
      scannedResult: '',
    };
  },
  mounted() {
    const qrCodeRegionId = "reader";

    this.html5QrCode = new Html5Qrcode(qrCodeRegionId);

    // Start scanning
    this.html5QrCode.start(
      { facingMode: "environment" }, // Use rear camera
      {
        fps: 10, // Scans per second
        qrbox: 250, // QR code scanning box size
      },
      (decodedText, decodedResult) => {
        // success callback when a QR code is scanned
        this.scannedResult = decodedText;
        console.log("Put your Qr Scan:", decodedText);
        this.html5QrCode.stop(); // Stop scanning once a code is found (optional)
      },
      (errorMessage) => {
        // failure callback for scan errors, ignored here
        console.warn("QR Code no match:", errorMessage);
      }
    ).catch((err) => {
      console.error("Unable to start scanning:", err);
    });
  },
  beforeDestroy() {
    // Clean up scanner on component destroy
    if (this.html5QrCode) {
      this.html5QrCode.stop().catch(() => {
        // ignore stop errors
      });
    }
  }
};
</script>

<style scoped>
#reader {
  margin: auto;
}
</style>
