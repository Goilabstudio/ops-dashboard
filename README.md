<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Ignition Labs – Ops Dashboard</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-white text-gray-900 p-6">
  <div class="max-w-4xl mx-auto">
    <h1 class="text-4xl font-bold mb-4">Ignition Labs – Ops Dashboard</h1>

    <div class="mb-6">
      <h2 class="text-2xl font-semibold mb-2">Daily Metrics</h2>
      <ul id="dailyMetrics" class="list-disc ml-6"></ul>
    </div>

    <div class="mb-6">
      <h2 class="text-2xl font-semibold mb-2">Weekly Progress</h2>
      <ul id="weeklyProgress" class="list-disc ml-6"></ul>
    </div>

    <div class="mb-6">
      <h2 class="text-2xl font-semibold mb-2">Top Performer</h2>
      <p id="topPerformer" class="text-lg font-medium"></p>
    </div>

    <footer class="mt-8 text-sm text-gray-600">
      © 2025 Ignition Labs. All rights reserved.
    </footer>
  </div>

  <script>
    // Dummy team data
    const data = {
      dailyMetrics: {
        "Calls Done": 26,
        "Calls Booked": 9,
        "Calls Attended": 7
      },
      weeklyProgress: {
        "New Leads": 53,
        "Follow-ups Done": 40,
        "Closures": 12
      },
      teamPerformance: [
        { name: "Rithik", calls: 14, closures: 4 },
        { name: "Anuj", calls: 12, closures: 5 },
        { name: "Pallavi", calls: 18, closures: 2 }
      ]
    };

    function renderList(id, items) {
      const container = document.getElementById(id);
      container.innerHTML = '';
      for (let key in items) {
        const li = document.createElement('li');
        li.innerHTML = `<strong>${key}:</strong> ${items[key]}`;
        container.appendChild(li);
      }
    }

    function getTopPerformer(team) {
      return team.sort((a, b) => (b.calls + b.closures) - (a.calls + a.closures))[0];
    }

    function renderDashboard() {
      renderList("dailyMetrics", data.dailyMetrics);
      renderList("weeklyProgress", data.weeklyProgress);

      const top = getTopPerformer(data.teamPerformance);
      document.getElementById("topPerformer").innerText =
        `${top.name} – ${top.calls} calls + ${top.closures} closures`;
    }

    renderDashboard();
  </script>
</body>
</html>
