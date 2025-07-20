<!DOCTYPE html>
<html>
  <body>
    <form id="locationForm">
      <input type="text" id="lat" placeholder="Latitude">
      <input type="text" id="lng" placeholder="Longitude">
      <input type="text" id="photo" placeholder="Photo URL">
      <button type="submit">Send to Sheet</button>
    </form>

    <script>
      const url = "https://script.google.com/macros/s/AKfycbxP-UI08rNQugCjUzvaGjUp179Ew-RpImQD6Utsnm3rjEqAzPbv0E-BLG_fxcBRa6_V/exec";

      document.getElementById("locationForm").addEventListener("submit", function(e) {
        e.preventDefault();
        const data = {
          latitude: document.getElementById("lat").value,
          longitude: document.getElementById("lng").value,
          photo: document.getElementById("photo").value
        };

        fetch(url, {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify(data)
        })
        .then(res => res.text())
        .then(msg => alert("✅ Data Saved: " + msg))
        .catch(err => alert("❌ Error: " + err));
      });
    </script>
  </body>
</html>
