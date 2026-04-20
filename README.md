<img width="1407" height="832" alt="image" src="https://github.com/user-attachments/assets/9f61ac21-e71f-4064-b9eb-2e60987a042d" />

<img width="2509" height="1406" alt="image" src="https://github.com/user-attachments/assets/e3a18293-1ffc-4405-8dbe-cd8179227344" />

---

## Table of Contents

### Getting Started
- [Resources](#resources)
- [What is Alloy? When does it make sense to use it?](#what-is-alloy-when-does-it-make-sense-to-use-it)
- [Alloy configuration language 101](#alloy-configuration-language-101)
- [Learning environment setup](#learning-environment-setup)

### Foundations (Training)
- [Foundation 1: Traces](#traces)
- [Foundation 2: Logs](#logs)
- [Foundation 3: Metrics](#metrics)
- [How to use the Alloy UI to debug pipelines](#how-to-use-the-alloy-ui-to-debug-pipelines)

### Missions (Challenges)
- [Mission I: Rogue Dimension](#mission-i-rogue-dimension) - cardinality filtering
- [Mission II: Operation Cold Storage](#mission-ii-operation-cold-storage) - log splitting & S3 archival
- [Mission III: Selective Surveillance](#mission-iii-selective-surveillance) - head sampling
- [Mission IV: Leave No (Error) Trace](#mission-iv-leave-no-error-trace) - tail sampling

### Reference
- [All Commands](#all-commands)
- [Troubleshooting](#troubleshooting)

---

# Resources

- [Grafana Alloy documentation](https://grafana.com/docs/alloy/latest/)
  - [Alloy configuration blocks](https://grafana.com/docs/alloy/latest/reference/config-blocks/)
  - [Alloy components](https://grafana.com/docs/alloy/latest/reference/components/)
  - [Collect and forward data with Grafana Alloy](https://grafana.com/docs/alloy/latest/collect/)
  - [Grafana Alloy Tutorials](https://grafana.com/docs/alloy/latest/tutorials/)

# What is Alloy? When does it make sense to use it?

<img width="2557" height="1413" alt="image" src="https://github.com/user-attachments/assets/75f0f830-636e-4c6e-a535-c8895acfd777" />

<img width="1438" height="806" alt="image" src="https://github.com/user-attachments/assets/2a495f57-66e8-4538-94a0-4c2cfbec1839" />

<img width="1440" height="808" alt="image" src="https://github.com/user-attachments/assets/e7481ed6-c40b-4912-8aff-fc3146f0a73e" />

<img width="1440" height="809" alt="image" src="https://github.com/user-attachments/assets/0a1b832b-5f4f-4d65-8bfe-df8444b5dc43" />

<img width="1439" height="812" alt="image" src="https://github.com/user-attachments/assets/f6686b9e-5c61-4e03-b37d-ac79949a7d82" />

<img width="1438" height="812" alt="image" src="https://github.com/user-attachments/assets/ca82350d-83f1-4ef2-9e35-743520a3d184" />

# Alloy configuration language 101

### Think of Alloy as our secret weapon that collects, transforms, and exports our telemetry data.

![Alt Text](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeTkyOTc1eW1idjM4MW1sbXNtbmZjNzBrcHIyZWo4bXg2dGcwdWNyciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Mb9dQnfZXSBYMhU2Nv/giphy.gif)

To instruct Alloy on how we want that done, we must write these instructions in a language (`Alloy syntax`) that Alloy understands.

<img width="2508" height="1409" alt="image" src="https://github.com/user-attachments/assets/427f1f24-0869-4d6a-87d5-5e91d5b0c9a9" />
<img width="2508" height="1407" alt="image" src="https://github.com/user-attachments/assets/ad4a092f-e914-48f5-aa78-a49b575eb912" />
<img width="2506" height="1409" alt="image" src="https://github.com/user-attachments/assets/9da4ee1f-6d41-4a52-a2d3-352702a30aa5" />
<img width="2508" height="1409" alt="image" src="https://github.com/user-attachments/assets/a9de2552-8654-44ac-ad9d-c6721884603b" />
<img width="2507" height="1408" alt="image" src="https://github.com/user-attachments/assets/3ea214f5-abeb-4798-b9ff-14d8f5c31d34" />
<img width="2509" height="1408" alt="image" src="https://github.com/user-attachments/assets/05b433bb-e80a-4205-9c1b-ade73650f2f0" />
<img width="2510" height="1410" alt="image" src="https://github.com/user-attachments/assets/b1ab4f30-736f-403b-b5a1-eca171d24f02" />
<img width="2510" height="1409" alt="image" src="https://github.com/user-attachments/assets/491e8022-904b-4c90-aac4-c83d0a75d756" />
<img width="2510" height="1404" alt="image" src="https://github.com/user-attachments/assets/aa299e50-4f2e-44d9-adc0-95aabd4ea9ac" />
<img width="2507" height="1409" alt="image" src="https://github.com/user-attachments/assets/1eb9b0c2-2b18-4ea5-a7f0-3035e6112e16" />
<img width="2504" height="1407" alt="image" src="https://github.com/user-attachments/assets/d344bd85-7d5b-4020-b063-554dcca8188f" />
<img width="2511" height="1409" alt="image" src="https://github.com/user-attachments/assets/1ad9451c-40f0-4b4d-bd0e-e4adcd70bb9d" />

The `usage` section gives you an example of how this particular component could be configured.

<img width="2510" height="1409" alt="image" src="https://github.com/user-attachments/assets/346cdf21-594d-4606-ab55-01dee9470e9a" />

The `arguments` and `blocks` sections list what you could do with the data. Pay close attention to the name, type, description, default, and required columns so Alloy could understand what you want it to do!

<img width="2508" height="1411" alt="image" src="https://github.com/user-attachments/assets/6a6102f6-82e9-4e31-bff6-faac9a5fcf6b" />

<img width="2509" height="1411" alt="image" src="https://github.com/user-attachments/assets/77f29151-513f-4258-8ad5-6c370ad9265a" />

Focusing on these 3 things will point us in the right direction as we configure our pipeline.
<img width="2506" height="1411" alt="image" src="https://github.com/user-attachments/assets/eeda8160-d3f6-4b9f-8ce7-52205c460f7e" />

# Learning environment setup

<img width="2506" height="1411" alt="image" src="https://github.com/user-attachments/assets/c188f4a8-4c43-4104-880a-6bf6de1f9ddf" />

> [!IMPORTANT]
> **Prerequisites**
>
> Make sure you have the following installed before continuing:
> - [Docker Desktop](https://www.docker.com/products/docker-desktop/) or [Docker Engine](https://docs.docker.com/engine/install/)
> - [Docker Compose](https://docs.docker.com/compose/install/) (included with Docker Desktop)

**Step 1:** Clone the repo for the learning environment:

```bash
git clone https://github.com/grafana/grafanacon2026-alloy-in-action.git
```

**Step 2:** Start the environment from within the project's root directory:

```bash
make start
```

You should see the following message in the terminal:

```
✅ Mission Control is online
Health check: curl http://localhost:8080/health
```

> [!TIP]
> To stop the environment at any time, run `make stop` from the project root.

### Verify the Setup

1. Open [Grafana (localhost:3000)](http://localhost:3000). You should see the Grafana page:
<img width="1165" height="597" alt="image" src="https://github.com/user-attachments/assets/957de535-29a9-4c31-8dc6-6d1dad4f89f8" />

2. Open [the Alloy UI (localhost:12347)](http://localhost:12347). You should see the Alloy UI:
<img width="1158" height="473" alt="image" src="https://github.com/user-attachments/assets/f4b1c71d-6f05-4c45-b8ee-6ec5d2bfb898" />

If both pages load, you're good to go!

> [!WARNING]
> **Setup not working?**
> - **Docker not running?**
>   If you're using Docker Desktop, start it (or restart it if it is already running) and try again. If you're using Docker Engine, make sure the Docker daemon is running (`sudo systemctl start docker`).
> - **Port conflicts?**
>   Make sure ports 3000, 12347, 4317, and 4318 are free.

### Open the Config File

Open the project using a text editor of your choice.

1. Expand the `alloy/` folder and open the `config.alloy` file.
2. We will use this file to build pipelines for the training exercises and missions.

> [!NOTE]
> Throughout this workshop, you'll edit `alloy/config.alloy` and then reload Alloy to apply your changes. Each section builds on the previous one, so keep your earlier work in the file as you add new pipelines.

# Foundations

## Traces

<img width="2501" height="1402" alt="image" src="https://github.com/user-attachments/assets/acf8e2cb-0820-4e3e-a85d-3358a4f1fa0d" />

### Objectives

- Use [`otelcol.receiver.otlp`](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.receiver.otlp/) to receive traces from the application
- Use [`otelcol.processor.batch`](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.processor.batch/) to batch traces for efficient export
- Use [`otelcol.exporter.otlphttp`](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.exporter.otlphttp/) to send traces to Tempo

### Scenario

Field agents are conducting operations around the world, and `mission-control` is tracking every request that flows through the system.
These operations generate **traces**, detailed records of each request's journey through the application.

Right now, those traces are being generated but going nowhere, since Alloy isn't configured to receive them.

**Your task:**
Build a trace pipeline so you can see what's happening inside mission-control.

Once it's configured, you'll be able to view traces in the Mission Control Grafana dashboard and drill into individual operations.

### Build the Pipeline

**Pipeline:**

`otelcol.receiver.otlp` → `otelcol.processor.batch` → `otelcol.exporter.otlphttp`

- Receive OTLP traces on `0.0.0.0:4317` (gRPC) and `0.0.0.0:4318` (HTTP)
- Batch traces before sending (improves efficiency)
- Export to Tempo at `http://tempo:4318`

### Starter Code

Copy this into your `config.alloy` file and fill in the TODOs:

> [!TIP]
> **How the starter code works:** Each exercise gives you a code block with `TODO` placeholders. Replace each `TODO` with the correct value. The comments next to each `TODO` give you a hint about what goes there.

```alloy
/*
  Foundation 1: Traces Pipeline
  Pipeline: otelcol.receiver.otlp -> otelcol.processor.batch -> otelcol.exporter.otlphttp
*/

// Step 1: Receive OTLP traces from mission-control

//The receiver listens for incoming traces. Mission-control sends traces using OTLP, so you need both gRPC and HTTP endpoints which are 4317 annd 4318 by default.
otelcol.receiver.otlp "default" {
  grpc {
    endpoint = "0.0.0.0:4317"
  }

  http {
    endpoint = "0.0.0.0:4318"
  }
// OpenTelemetry components use `output` to send data and `.input` to receive it:
  output {
    traces = [TODO]  // Forward to the batch processor's input hint: component_type.label.input
  }
}

// Step 2: Batch traces before exporting

otelcol.processor.batch "default" {
  send_batch_size     = 100
  send_batch_max_size = 200
  timeout             = "250ms"

  output {
    traces = [TODO]  // Forward to the Tempo exporter's input
  }
}


// Step 3: Export traces to Tempo

otelcol.exporter.otlphttp "docker_tempo" {
  client {
    endpoint = "TODO"  // Send to http://tempo:4318
    tls {
      insecure             = true
      insecure_skip_verify = true
    }
  }
}
```

<details>
<summary>Full solution</summary>
  
```alloy
/*
  Foundation 1: Traces Pipeline
  Pipeline: otelcol.receiver.otlp -> otelcol.processor.batch -> otelcol.exporter.otlphttp
*/
// Receive OTLP traces from mission-control
otelcol.receiver.otlp "default" {
  grpc {
    endpoint = "0.0.0.0:4317"
  }
  http {
    endpoint = "0.0.0.0:4318"
  }
  output {
    traces = [otelcol.processor.batch.default.input]
  }
}
// Batch traces before exporting
otelcol.processor.batch "default" {
  output {
    traces = [otelcol.exporter.otlphttp.docker_tempo.input]
  }
}
// Export traces to Tempo
otelcol.exporter.otlphttp "docker_tempo" {
  client {
    endpoint = "http://tempo:4318"
    tls {
      insecure             = true
      insecure_skip_verify = true
    }
  }
}
```
</details>

### Reloading the Config

Whenever you make changes to the config file, you need to reload Alloy:

```bash
make alloy-reload
```

If the config is valid, you'll see:

```
config reloaded
```

> [!CAUTION]
> If you see an error instead of `config reloaded`, double-check your config for typos, missing commas, or smart quotes. See the [Troubleshooting](#troubleshooting) section for common issues.

### Verify Your Work

1. Go to the [Mission Control Overview dashboard (localhost:3000)](http://localhost:3000/d/mission-control-overview/mission-control-overview). The Traces panel at the bottom should now show data.

<img width="2512" height="1411" alt="image" src="https://github.com/user-attachments/assets/33dc061c-b87f-4c77-b4d5-4947509d5f65" />

2. When you click on one of the traces, you can see the full breakdown of what happened and how long it took.

<img width="2511" height="1414" alt="image" src="https://github.com/user-attachments/assets/21b3c77c-c918-4e77-bb7f-b7969da3485a" />

## Logs

### Objectives

<img width="1866" height="1048" alt="image" src="https://github.com/user-attachments/assets/4b5e5448-96b4-4935-97d0-ceb86d70c033" />

- Use [`loki.source.file`](https://grafana.com/docs/alloy/latest/reference/components/loki/loki.source.file/) to discover and read log files
- Use [`loki.process`](https://grafana.com/docs/alloy/latest/reference/components/loki/loki.process/) to parse JSON and extract labels
- Use [`loki.write`](https://grafana.com/docs/alloy/latest/reference/components/loki/loki.write/) to send logs to Loki

### Scenario

Mission-control generates operational logs: JSON-formatted records of everything happening in the system. Agent check-ins, status updates, and internal events.

These logs are written to files inside the container but no one's reading them, just like the previous section.

The environment is set up to mimic a scenario where Alloy is running on and has access to the machine's filesystem (a Daemonset in Kubernetes or simply an Alloy
collector running on each VM).

**Your task:**
Build a log pipeline to read mission-control's log files, parse the JSON, and send them to Loki.

Once it's configured, you'll see logs flowing into Grafana where you can search and filter by component.

### Build the Pipeline

**Pipeline:**

`loki.source.file` → `loki.process` → `loki.write`

- Discover and read log files at `/var/log/alloy/*.log`
- Parse JSON and extract the `component` field and add it as a label
- Write to Loki at `http://loki:3100/loki/api/v1/push`

### Starter Code

Add this to your `config.alloy` file (below your traces pipeline) and fill in the TODOs:

```alloy
/*
  Foundation 2: Logs Pipeline
  Pipeline: loki.source.file -> loki.process -> loki.write
*/
// Step 1: Discover and read files

loki.source.file "mission_control" {
  targets    = [{"__path__" = "/var/log/alloy/*.log"}]

  file_match {
    enabled = true
  }

  forward_to = [TODO]  // Forward to loki.process receiver
}

/*
Step 2: Extract "component" from JSON and promote to label
Original log: {"level":"INFO","component":"agents","msg":"Request received"}
Labels are indexed - makes filtering fast in Grafana
*/

loki.process "mission_control_logs" {
//`stage.json` parses the log body
  stage.json {
    expressions = {
      component = "component",    // Extract the "component" field from the JSON log body
    }
  }

// Add the extracted field as a Loki label
//`stage.labels` adds extracted fields to Loki labels
  stage.labels {
    values = {
      component = "",  // Empty string means "use the extracted value with the same name."
    }
  }

  forward_to = [TODO]  // Forward to the loki.write receiver
}

// Step 3: Send logs to Loki

loki.write "docker_loki" {
  endpoint {
    url = "http://loki:3100/loki/api/v1/push"
  }
}
```

<details>
<summary>Full solution</summary>

```alloy
/*
  Foundation 2: Logs Pipeline
  Pipeline: loki.source.file -> loki.process -> loki.write
*/

// Discover and read log files
loki.source.file "mission_control" {
  targets    = [{"__path__" = "/var/log/alloy/*.log"}]

  file_match {
    enabled = true
  }

  forward_to = [loki.process.mission_control_logs.receiver]
}

// Parse JSON logs and extract labels
loki.process "mission_control_logs" {
  stage.json {
    expressions = {
      component = "component",
    }
  }

  stage.labels {
    values = {
      component = "",
    }
  }

  forward_to = [loki.write.docker_loki.receiver]
}

// Send logs to Loki
loki.write "docker_loki" {
  endpoint {
    url = "http://loki:3100/loki/api/v1/push"
  }
}
```

</details>

> [!TIP]
> You can also use [`local.file_match`](https://grafana.com/docs/alloy/latest/reference/components/local/local.file_match/) to perform file discovery. This used to be the only way to do it. However, using the `file_match` block inside `loki.source.file` has less overhead and results in a simpler pipeline.

### Reload and Verify

> [!IMPORTANT]
> Remember to reload Alloy after every config change: `make alloy-reload`

### Verify Your Work

1. Check the [Mission Control Overview dashboard (localhost:3000)](http://localhost:3000/d/mission-control-overview/mission-control-overview). The logs panel should now show data.

<img width="2507" height="1407" alt="image" src="https://github.com/user-attachments/assets/3f1eb1ba-987b-4418-822c-b8210c408bc1" />

2. Next, open Explore from the Grafana sidebar.

   Explore is Grafana's query playground. It lets you run ad-hoc queries without building a dashboard.

3. Select **Loki** as the data source and try this query:

   ```
   {component="agents"}
   ```

4. You should see logs filtered to just field agent activity.
<img width="2509" height="1405" alt="image" src="https://github.com/user-attachments/assets/ce5b5337-78da-4eb1-b17e-0859435b046b" />

5. Check `Common labels` at the top. It shows `component=agents`. That's the label we extracted from the JSON.

> [!TIP]
> **Why labels matter:** Without that label, you'd have to search the entire log body to filter by component. With it, you can filter instantly. Labels are indexed in Loki, making queries fast and efficient.

## Metrics

<img width="2510" height="1409" alt="image" src="https://github.com/user-attachments/assets/26bd91f6-50af-41cf-9868-1c493b91edeb" />

### Objectives

- Use [`prometheus.scrape`](https://grafana.com/docs/alloy/latest/reference/components/prometheus/prometheus.scrape/) to scrape metrics from the application
- Use [`prometheus.relabel`](https://grafana.com/docs/alloy/latest/reference/components/prometheus/prometheus.relabel/) to standardize label names for consistency
- Use [`prometheus.remote_write`](https://grafana.com/docs/alloy/latest/reference/components/prometheus/prometheus.remote_write/) to export metrics to Mimir

### Scenario

The `mission-control` application exposes a set of metrics in Prometheus format, accessible at the standard `/metrics` endpoint. Among those metrics are agent check-ins, used to track
which field operatives are active and where they're located.

**Your task:**
Build a metrics pipeline to scrape `mission-control`, standardize the labels, and send them to Mimir.

Once it's configured, you'll see a world map showing agent locations, grouped by country.

### The Problem

Two metrics track your agents: `active_agents` tells you who's currently online, and `agent_comms_total` counts their check-ins. Together, they paint a picture of field activity.

But these metrics label the same data differently. `active_agents` uses `agent_id` and `country_code`, while `agent_comms_total` uses `id` and `region`. This makes it harder to correlate metrics later. You'll use `prometheus.relabel` to standardize them.

This kind of inconsistency is common as organizations grow and teams or departments develop different observability practices. Luckily, it's all solvable at the collector level!

### Build the Pipeline

**Pipeline:**

`prometheus.scrape` → `prometheus.relabel` → `prometheus.remote_write`

- Scrape metrics from `mission-control:8080`
- Rename `id` → `agent_id` and `region` → `country_code`
- Send to Mimir at `http://mimir:9009/api/v1/push`

### Starter Code

Add this to your `config.alloy` file (below your logs pipeline) and fill in the TODOs:

```alloy
/*
  Foundation 3: Metrics Pipeline
  Pipeline: prometheus.scrape -> prometheus.relabel -> prometheus.remote_write
*/

// Step 1: Scrape metrics from mission-control

prometheus.scrape "mission_control" {
  scrape_interval = "5s"
  scrape_timeout  = "4s"

  targets    = [{"__address__" = "mission-control:8080"}]
  forward_to = [TODO]  // Forward to prometheus.relabel.standardize_agent_labels receiver
}

// Step 2: Standardize label names

/*
  Standardize labels so all agent metrics use consistent naming

  Before:
    active_agents{agent_id="ALPHA-007", country_code="US"}
    agent_comms_total{id="ALPHA-007", region="US"}

  After:
    active_agents{agent_id="ALPHA-007", country_code="US"}
    agent_comms_total{agent_id="ALPHA-007", country_code="US"}

  Rename: id -> agent_id, region -> country_code
*/

prometheus.relabel "standardize_agent_labels" {
  rule {
    action        = "replace"
    source_labels = ["id"]
    regex         = "(.+)"
    target_label  = "agent_id"
  }

  rule {
    action = "labeldrop"
    regex  = "^id$"
  }

  // We'll do the same with the "region" label to rename it to "country_code" and drop the old label

  rule {
    action        = "replace"
    source_labels = ["TODO"]
    regex         = "(.+)"
    target_label  = "TODO"
  }

  rule {
    action = "labeldrop"
    regex  = "^TODO$"
  }

  forward_to = [TODO]  // Forward to prometheus.remote_write receiver
}

// Step 3: Send metrics to Mimir

prometheus.remote_write "docker_mimir" {
  endpoint {
    url = "http://mimir:9009/api/v1/push"
  }
}

```

<details>
<summary>Full solution</summary>

```alloy
/*
  Foundation 3: Metrics Pipeline
  Pipeline: prometheus.scrape -> prometheus.relabel -> prometheus.remote_write
*/

// Scrape metrics from mission-control
prometheus.scrape "mission_control" {
  scrape_interval = "5s"
  scrape_timeout  = "4s"

  targets    = [{"__address__" = "mission-control:8080"}]
  forward_to = [prometheus.relabel.standardize_agent_labels.receiver]
}

// Step 2: Standardize label names

/*
  Standardize labels so all agent metrics use consistent naming

  Before:
    active_agents{agent_id="ALPHA-007", country_code="US"}
    agent_comms_total{id="ALPHA-007", region="US"}

  After:
    active_agents{agent_id="ALPHA-007", country_code="US"}
    agent_comms_total{agent_id="ALPHA-007", country_code="US"}

  Rename: id → agent_id, region → country_code
*/

prometheus.relabel "standardize_agent_labels" {
  rule {
    action        = "replace"
    source_labels = ["id"]
    regex         = "(.+)"
    target_label  = "agent_id"
  }

  rule {
    action = "labeldrop"
    regex  = "^id$"
  }

  rule {
    action        = "replace"
    source_labels = ["region"]
    regex         = "(.+)"
    target_label  = "country_code"
  }

  rule {
    action = "labeldrop"
    regex  = "^region$"
  }
  forward_to = [prometheus.remote_write.docker_mimir.receiver]  // Forward to prometheus.remote_write receiver
}

// Step 3: Send metrics to Mimir
prometheus.remote_write "docker_mimir" {
  endpoint {
    url = "http://mimir:9009/api/v1/push"
  }
}
```

</details>

### Reload and Verify

> [!IMPORTANT]
> Remember to reload Alloy after every config change: `make alloy-reload`

### Verify Your Work

1. Check the [Mission Control Overview dashboard (localhost:3000)](http://localhost:3000/d/mission-control-overview/mission-control-overview) and view the Active Agents panel.
<img width="2508" height="1409" alt="image" src="https://github.com/user-attachments/assets/6088be81-95ea-427a-8f0d-2d2ff41b7660" />

2. To verify your relabel rules are working, go to Explore, select **Mimir** as a data source and run this query:

   ```
   agent_comms_total{agent_id=~".+"}
   ```

3. You should see that `agent_comms_total` metric now has `agent_id` and `country_code` labels (purple box). That confirms that our relabeling rules worked.
<img width="2506" height="1410" alt="image" src="https://github.com/user-attachments/assets/5fd78140-ef2a-4763-9058-67063bf62205" />

### How to use the Alloy UI to debug pipelines

Alloy's UI is a useful tool that helps you visualize how Alloy is configured and what it is doing so you are able to debug efficiently.

Navigate to [localhost:12347](http://localhost:12347) to see the list of components (orange box) that alloy is currently configured with.
Click on the blue ‘view’ button on the right side (red arrow).
<img width="2506" height="1402" alt="image" src="https://github.com/user-attachments/assets/3d2c591c-2519-4aed-8f8b-7072b7a0dd91" />

This page shows us the health of the component, the arguments it's using, and its current exports (green box).

This page also gives us quick access to the component’s documentation (orange arrow) and a Live Debugging view (yellow arrow).
<img width="2501" height="1407" alt="image" src="https://github.com/user-attachments/assets/9ce8d733-7f14-4686-b128-248f2a0faa37" />

When we click on the `Live Debugging` view, we will be able to see a real-time stream of telemetry flowing through a component.
<img width="2509" height="1411" alt="image" src="https://github.com/user-attachments/assets/ae97f9a3-574a-4d15-a67c-5667e2dbca40" />

Navigate to the `Graph` tab to access the graph of components and how they are connected.
<img width="2512" height="1410" alt="image" src="https://github.com/user-attachments/assets/78ec39b1-1413-4d16-ab72-6a682d199bb2" />

The number (pink box) shown on the dotted lines shows the rate of transfer between components. The window at the top (pink box) configures the interval over which Alloy should calculate the per-second rate, so a window of ‘5’ means that Alloy should look over the last 5 seconds to compute the rate.

The color of the dotted line signifies what type of data are being transferred between components. See the color key (green box) for clarification.

> [!TIP]
> **Quick debugging checklist with the Alloy UI:**
> 1. Ensure that no component is reported as unhealthy.
> 2. Ensure that the arguments and exports for misbehaving components appear correct.
> 3. Use live debugging to verify the data is what you expect.

---

# Break

> [!NOTE]
> **Nice work completing the foundations!**
>
> You now have a working pipeline for traces, logs, and metrics.
>
> If you got stuck on any foundation, you can copy a checkpoint file to catch up:
> ```bash
> cp alloy/checkpoints/foundation3.alloy alloy/config.alloy
> make alloy-reload
> ```

---

# Missions

Training's over. Each mission throws a new crisis at the pipelines you've built. Activate with `make missionN`, reset all with `make reset`.

## Mission I: Rogue Dimension

```bash
make mission1
```

<img width="2513" height="1411" alt="image" src="https://github.com/user-attachments/assets/418058d0-ff9c-41e6-b823-a3fd25b624de" />

An adversary discovered that our server records the full request path as a metric label. They're now flooding us with requests to thousands of random URLs, paths like `/api/a3f8c2e1` that don't map to any real endpoint. Every unique path creates a new time series in Mimir, and cardinality is climbing fast.

**Your orders:**
You'll be expanding on what you did in the Metrics foundation. There is a pre-made regular expression provided for you to use at `http://mission-control:8080/api/metrics/allowed-paths`. Use `prometheus.relabel` with a `keep` action on the `path` label to filter out the garbage. The [Alloy standard library](https://grafana.com/docs/alloy/latest/reference/stdlib/) functions may be helpful here!

<img width="2504" height="1407" alt="image" src="https://github.com/user-attachments/assets/6e3da07a-2b2f-47d8-b673-0bd6a0636860" />

### Before You Start

Open [Explore in Grafana (localhost:3000/explore)](http://localhost:3000/explore), select **Mimir** as the data source, and run:

```
http_requests_total
```

If the query times out, try narrowing the time range to **Last 5 minutes**. That's the cardinality explosion in action. 

Scroll through the series list and notice the random paths like `/api/a3f8c2e1` with `status="404"`. After you apply the fix, you should only see legitimate paths.

### Starter Code

Add these components to your metrics section (below `standardize_agent_labels`) and fill in the TODOs. Relabeling must happen **before** `remote_write` so only allowed `path` labels reach Mimir.

```alloy
/*
  Mission I: Rogue Dimension
  Pipeline: remote.http -> prometheus.relabel -> prometheus.remote_write
*/

// Step 1: Fetch the allowlist of legitimate paths
remote.http "allowed_paths_regex" {
  url = "http://mission-control:8080/api/metrics/allowed-paths"
}

// Step 2: Filter - only keep metrics where "path" is a known legitimate route
prometheus.relabel "mission1" {
  rule {
    action        = "keep"
    source_labels = ["path"]
    regex         = TODO
  }

  forward_to = [prometheus.remote_write.docker_mimir.receiver]
}

```

<details>
<summary>Hint 1: you don't need to write regex</summary>

The API at `http://mission-control:8080/api/metrics/allowed-paths` returns a **ready-made regex** for you.

Try looking at the endpoint to see what the response looks like: [localhost:8080/api/metrics/allowed-paths](http://localhost:8080/api/metrics/allowed-paths)


Use `localhost` when curling from your terminal. Inside the Alloy config, use `mission-control`, which is the Docker-internal hostname.

</details>

<details>
<summary>Hint 2: accessing the response body</summary>

`remote.http` exposes the fetched response body as `.content`. You can pass it to standard library functions or other components!

</details>

<details>
<summary>Hint 3: parsing the response</summary>

The response body is JSON, not a plain string. Use `encoding.from_json()` from the [Alloy standard library](https://grafana.com/docs/alloy/latest/reference/stdlib/encoding/) to parse it into an object you can access.

</details>

<details>
<summary>Hint 4: putting it together</summary>

In Alloy, you can chain expressions together. The general pattern for this particular exercise looks like:

```
encoding.from_json(some_component.content).some_field
```

Parse the content, then access the field you need with dot notation.

</details>

<details>
<summary>Hint 5: pipeline order</summary>

Scraped metrics should flow through your **standardize** relabel component, then through this new `keep` filter, then `remote_write`. If the filter is bypassed, cardinality in Mimir will not improve.

</details>

<details>
<summary>Full solution</summary>

```alloy
// Fetch the allowlist (unchanged)
remote.http "allowed_paths_regex" {
  url = "http://mission-control:8080/api/metrics/allowed-paths"
}

// Filter: only keep series whose `path` label matches the allowlist
prometheus.relabel "mission1" {
  rule {
    action        = "keep"
    source_labels = ["path"]
    regex         = encoding.from_json(remote.http.allowed_paths_regex.content).regex
  }

  forward_to = [prometheus.remote_write.docker_mimir.receiver]
}
```

Make sure to rewire the existing `standardize_agent_labels` component so metrics flow through the new filter before reaching Mimir:

```alloy
prometheus.relabel "standardize_agent_labels" {
  // ...existing rules unchanged...

  forward_to = [prometheus.relabel.mission1.receiver]
}
```

**How it works**

- `remote.http.allowed_paths_regex.content` exposes the raw response body from the fetched URL, a JSON string like `{"regex":"^(/api/agents|/metrics|...)$"}`.
- [`encoding.from_json`](https://grafana.com/docs/alloy/latest/reference/stdlib/encoding/) parses that string into an object so you can reach into it. Chaining `.regex` pulls the pre-built pattern out of the object.
- The `keep` action tells `prometheus.relabel` to drop every series whose `path` label does not match the regex, so the attacker's random `/api/a3f8c2e1`-style paths never make it to `remote_write`.
- The final pipeline is `scrape -> standardize_agent_labels -> mission1 -> remote_write`. Make sure `standardize_agent_labels.forward_to` points at `prometheus.relabel.mission1.receiver` so the filter sits in the path.

</details>

### Verify Your Work

> [!NOTE]
> After reloading, give it **~20 seconds** for scraped metrics to flow through the pipeline and land in Mimir before verifying.

```bash
make mission1-verify
```

Then you can confirm with the Alloy livedebugging view:

1. Navigate to [the Alloy UI (localhost:12347)](http://localhost:12347)
2. Click on `View` for `prometheus.remote_write.docker_mimir`
3. Click `livedebugging` at the top, under the component identifier
4. Wait for one scrape to come in and click `Stop` on the top right
5. In the search bar, enter `http_requests_total` to filter for only the relevant samples

You should see only **legitimate paths** (like `/api/agents`, `/metrics`, etc.). No more random paths!

>[!TIP] Once you're done, you can run `make mission1-stop` to lower the cardinality again

## Mission II: Operation Cold Storage

```bash
make mission2
```

<img width="2509" height="1410" alt="image" src="https://github.com/user-attachments/assets/001ea468-26d0-46b2-bca2-4d94fd96c680" />

After the last incident, the higher-ups want us to collect the `DEBUG` logs we were previously dropping. It turns out those include request logs that could have helped us track down the attacker. But pumping everything into Loki would blow the budget. The directive: archive _all_ logs to a new S3 bucket named `audit-logs`, but only send `INFO`/`WARN`/`ERROR` logs to Loki for fast queries.

**Your orders:**
The skills you picked up in Foundation II will come in handy here. Split your log pipeline into two parallel paths:

1. **All logs** -> S3 via `otelcol.receiver.loki` -> `otelcol.processor.batch` -> `otelcol.exporter.awss3`
2. **Non-DEBUG only** -> Loki via a second `loki.process` and using a `stage.drop` to drop any `DEBUG` logs

<img width="2511" height="1411" alt="image" src="https://github.com/user-attachments/assets/ce6e21b3-4c1e-41db-b9ed-a1450fef230a" />

### Starter Code

Extend your logs section (below `loki.process.mission_control_logs`). Update its `forward_to` to fan out to two destinations, then add the components below and fill in the TODOs.

```alloy
/*
  Mission II: Operation Cold Storage
  Pipeline:
    Path 1 (all logs): otelcol.receiver.loki -> otelcol.processor.batch -> otelcol.exporter.awss3
    Path 2 (non-DEBUG): loki.process -> loki.write
*/

// TODO: update loki.process.mission_control_logs forward_to with two receivers

// Path 1: Bridge Loki logs to OTLP format for S3 export
otelcol.receiver.loki "all_logs" {
  output {
    logs = [TODO]
  }
}

otelcol.processor.batch "s3_logs" {
  timeout             = "10s"
  send_batch_size     = 100
  send_batch_max_size = 200

  output {
    logs = [TODO]
  }
}

otelcol.exporter.awss3 "audit_logs" {
  s3_uploader {
    s3_bucket = "TODO"
    s3_prefix = "logs"

    endpoint            = "http://localstack:4566"
    disable_ssl         = true
    s3_force_path_style = true
  }

  marshaler {
    type = "body"
  }

  sending_queue {
    batch {
      flush_timeout = "500ms"
      min_size      = 100
      sizer         = "items"
    }
  }
}

// Path 2: Filter logs before sending to Loki
loki.process "filter_debug" {
  stage.json {
    expressions = {
      // Which JSON field contains the log level? Try using livedebugging to see what an example log line looks like!
      level = "TODO",
    }
  }

  // TODO: add a stage to drop the logs you don't want forwarded to Loki

  forward_to = [loki.write.docker_loki.receiver]
}
```

> [!NOTE]
> **Why OTLP components for Path 1?**
> The S3 exporter (`otelcol.exporter.awss3`) is an OpenTelemetry component. There's no native Loki component for writing to S3. To bridge the gap, `otelcol.receiver.loki` accepts Loki log entries and converts them to OTLP format, so they can flow through the `otelcol` pipeline to S3.

<details>
<summary>Hint 1: wiring the fan-out</summary>

`forward_to` takes an array, so you can list multiple receivers to send logs to both paths simultaneously. `otelcol.receiver.loki` exposes a `.receiver` export that accepts Loki log entries.

</details>

<details>
<summary>Hint 2: filtering logs</summary>

Check the [`loki.process` docs](https://grafana.com/docs/alloy/latest/reference/components/loki/loki.process/) for stages that can filter log lines based on an extracted field value.

</details>

<details>
<summary>Hint 3: stage details</summary>

The stage can take a `source` (the extracted field to compare) and `value` (the string to match against) to directly compare the value. Only
`source` and `value` are necessary for this mission, but it is possible to perform more complex matching.

</details>

<details>
<summary>Full solution</summary>

Update `loki.process.mission_control_logs` so its `forward_to` fans out to both paths:

```alloy
loki.process "mission_control_logs" {
  // ...existing stage.json and stage.labels unchanged...

  forward_to = [
    otelcol.receiver.loki.all_logs.receiver,   // Path 1: all logs -> S3
    loki.process.filter_debug.receiver,        // Path 2: non-DEBUG -> Loki
  ]
}
```

Path 1 (archive everything to S3):

```alloy
otelcol.receiver.loki "all_logs" {
  output {
    logs = [otelcol.processor.batch.s3_logs.input]
  }
}

otelcol.processor.batch "s3_logs" {
  timeout             = "10s"
  send_batch_size     = 100
  send_batch_max_size = 200

  output {
    logs = [otelcol.exporter.awss3.audit_logs.input]
  }
}

otelcol.exporter.awss3 "audit_logs" {
  s3_uploader {
    s3_bucket = "audit-logs"
    s3_prefix = "logs"

    endpoint            = "http://localstack:4566"
    disable_ssl         = true
    s3_force_path_style = true
  }

  marshaler {
    type = "body"
  }

  sending_queue {
    batch {
      flush_timeout = "500ms"
      min_size      = 100
      sizer         = "items"
    }
  }
}
```

Path 2 (drop DEBUG before Loki):

```alloy
loki.process "filter_debug" {
  stage.json {
    expressions = {
      level = "level",
    }
  }

  stage.drop {
    source = "level"
    value  = "DEBUG"
  }

  forward_to = [loki.write.docker_loki.receiver]
}
```

**How it works**

- `forward_to` accepts a list, so listing both receivers in `loki.process.mission_control_logs` fans every log line out to both downstream paths simultaneously.
- **Path 1 (S3 archive):** The S3 exporter is an OpenTelemetry component, so Loki-format entries have to be converted first. [`otelcol.receiver.loki`](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.receiver.loki/) accepts Loki entries and emits them as OTLP logs. From there the pipeline is a standard OTel chain: `batch` holds entries up to 10s or 100 items to keep the S3 object count sane, and `awss3` writes them to the `audit-logs` bucket under a `logs/year=.../month=...` prefix. The `endpoint` override points the exporter at the local localstack container instead of real AWS.
- **Path 2 (filtered Loki):** `stage.json` pulls the `level` field out of the JSON body and stores it in the stage's extracted map under the key `level`. `stage.drop` then references that same key: `source = "level"` tells it which extracted field to look at, and `value = "DEBUG"` is the string to compare against. Conceptually it is evaluating `extracted["level"] == "DEBUG"`, and any line that matches is dropped. Everything else (INFO, WARN, ERROR) is forwarded to `loki.write.docker_loki`, the same Loki sink you wired up in the Logs foundation.
- The result is a tiered storage pattern: all logs are archived cheaply in S3 for compliance and post-incident forensics, and only the higher-signal levels are indexed in Loki for interactive querying.

</details>

### Verify Your Work

```bash
make mission2-verify
```

Then confirm both paths manually:

**Path 2 (Loki, no DEBUG):** Open [Explore in Grafana (localhost:3000/explore)](http://localhost:3000/explore), select **Loki**, and set the time range to **Last 5 minutes**. Run:

```
{filename=~".+"}
```

You should still see `INFO` logs but no `DEBUG` logs in the time since you reloaded your Alloy config.

**Path 1 (S3, all logs):** Run `make s3-list` in your terminal. Look for:

- **File keys** like `logs/year=2026/month=04/day=13/hour=21/minute=54/logs_...txt` show log files are being written to S3 organized by timestamp
- **DEBUG entries** in the content (`"level":"DEBUG"`) mixed with INFO and WARN confirms S3 is receiving all logs, not just the filtered ones that go to Loki

## Mission III: Selective Surveillance

```bash
make mission3
```

<img width="2506" height="1410" alt="image" src="https://github.com/user-attachments/assets/7e06835d-2fe1-4ae2-87af-bb9623913bd5" />

We need to keep our network traffic to a minimum to maintain a low profile. Right now we're sending every single trace to Tempo, and that kind of volume is going to attract attention.

**Your orders:**
Go back to the pipeline you built in Foundation I and add head sampling to cut the volume down. Insert an `otelcol.processor.probabilistic_sampler` component between the OTLP receiver and batch processor. Set `sampling_percentage = 5.0` to keep only 5% of traces. While you're at it, think about what we're trading away here. What intelligence might slip through the cracks?
<img width="2502" height="1405" alt="image" src="https://github.com/user-attachments/assets/ba811483-6c22-4aec-b5cf-b4ab7700b85a" />

### Before You Start

Open [the Alloy UI (localhost:12347)](http://localhost:12347), click the **Graph** tab, and note the **trace rate** on the edges leading to Tempo. You'll compare this to the rate after you add sampling.

### Starter Code

Add this [`otelcol.processor.probabilistic_sampler`](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.processor.probabilistic_sampler/) component to your `config.alloy` and fill in the TODOs. Traces should enter the sampler **before** the batch processor.

```alloy
/*
  Mission III: Selective Surveillance
  Pipeline: otelcol.receiver.otlp -> otelcol.processor.probabilistic_sampler -> otelcol.processor.batch -> otelcol.exporter.otlphttp
*/

otelcol.processor.probabilistic_sampler "mission3" {
  sampling_percentage = TODO

  output {
    traces = [TODO]
  }
}
```

<details>
<summary>Hint: wiring</summary>

OTLP components use `.input` to receive data, just like you wired the batch processor in the foundations.

</details>

<details>
<summary>Full solution</summary>

Update the existing `otelcol.receiver.otlp "default"` so traces flow into the sampler before the batch processor:

```alloy
otelcol.receiver.otlp "default" {
  // ...grpc and http blocks unchanged...

  output {
    traces = [otelcol.processor.probabilistic_sampler.mission3.input]
  }
}
```

Add the sampler itself, forwarding survivors to the existing batch processor:

```alloy
otelcol.processor.probabilistic_sampler "mission3" {
  sampling_percentage = 5.0

  output {
    traces = [otelcol.processor.batch.default.input]
  }
}
```

**How it works**

- The sampler makes a keep-or-drop decision the instant a trace enters the collector. By default, that decision is derived from a hash of the trace ID, so it is deterministic: any collector that sees spans from the same trace will arrive at the same verdict, and traces stay intact rather than getting partially exported.
- `sampling_percentage = 5.0` keeps roughly 1 in every 20 traces. The other 95% are dropped immediately and never reach the batch processor, which is why volume to Tempo falls off sharply after reload.
- Trade-off: head sampling is cheap and stateless, but it is blind to what happens inside the trace. A trace that contains a 500 error has the same 5% survival odds as a healthy trace, which is what the "needle-in-a-haystack" warning is pointing at. Mission IV addresses this by swapping to tail sampling, where the decision can be based on the trace's contents.
- Make sure `otelcol.receiver.otlp.default.output.traces` points at `otelcol.processor.probabilistic_sampler.mission3.input`. If it still points straight at the batch processor, the sampler is bypassed entirely.

</details>

### Verify Your Work

```bash
make mission3-verify
```

Then confirm in the Alloy UI: go to [the Alloy UI (localhost:12347)](http://localhost:12347), click the **Graph** tab, and check the trace rate on the edges leading to Tempo. You should see a **significant drop** compared to before.

## Mission IV: Leave No (Error) Trace

```bash
make mission4
```

<img width="2510" height="1410" alt="image" src="https://github.com/user-attachments/assets/54db1bff-6bab-4403-b7ae-52e7ea1b3078" />

A field agent has sent us an encrypted dead drop and is transmitting the decryption key in fragments through span attributes on error traces. One piece every 15 seconds, five pieces total. With Head Sampling it will take too long to assemble the key.

**Your orders:**
Swap out the head sampler for `otelcol.processor.tail_sampling`. Configure two policies:

1. `status_code` policy: keep all error traces (every fragment counts)
2. `probabilistic` policy: sample 5% of everything else

Once you've recovered all the fragments, piece together the token and crack open the dead drop.

```bash
make access-token                 # Check token fragment recovery (wait ~75s)
make deaddrop KEY="your-token"    # Unlock the dead drop with the assembled token
```

<img width="2508" height="1410" alt="image" src="https://github.com/user-attachments/assets/bbd15e2c-1971-44b2-b5cf-59a00a3160c0" />

> [!IMPORTANT]
> Before adding tail sampling, remove the head sampler from Mission III. You can either delete it, comment it out, or rewire the pipeline to skip it.

### Starter Code

Add tail sampling to your trace pipeline and fill in the TODOs. Point the OTLP receiver at this processor, then continue to batch and send to Tempo as before.

```alloy
/*
  Mission IV: Leave No (Error) Trace
  Pipeline: otelcol.receiver.otlp -> otelcol.processor.tail_sampling -> otelcol.processor.batch -> otelcol.exporter.otlphttp
*/

otelcol.processor.tail_sampling "mission4" {
  decision_wait = "10s"

  policy {
    name = "keep_all_errors"
    type = "TODO"

    // TODO: add the inner block for this policy type
  }

  policy {
    name = "sample_normal_traffic"
    type = "TODO"

    // TODO: add the inner block for this policy type
  }

  output {
    traces = [otelcol.processor.batch.default.input]
  }
}
```

<details>
<summary>Hint 1: policy types</summary>

Check the [`otelcol.processor.tail_sampling` docs](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.processor.tail_sampling/) for the available policy types. You need one that matches on span status, and one that samples by percentage.

</details>

<details>
<summary>Hint 2: inner block structure</summary>

Each policy type has a corresponding inner block with the same name as the type, containing that type's arguments. For example:

```alloy
policy {
  name = "example"
  type = "latency"

  latency {
    threshold_ms = 5000
  }
}
```

</details>

<details>
<summary>Hint 3: error status codes</summary>

The [`status_code` block](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.processor.tail_sampling/#status_code) lists the valid values for `status_codes`.

</details>

<details>
<summary>Full solution</summary>

Update the existing `otelcol.receiver.otlp "default"` so traces flow into the tail sampler instead of the head sampler from Mission III:

```alloy
otelcol.receiver.otlp "default" {
  // ...grpc and http blocks unchanged...

  output {
    traces = [otelcol.processor.tail_sampling.mission4.input]
  }
}
```

Add the tail sampler with both policies, forwarding kept traces to the existing batch processor:

```alloy
otelcol.processor.tail_sampling "mission4" {
  decision_wait = "10s"

  policy {
    name = "keep_all_errors"
    type = "status_code"

    status_code {
      status_codes = ["ERROR"]
    }
  }

  policy {
    name = "sample_normal_traffic"
    type = "probabilistic"

    probabilistic {
      sampling_percentage = 5.0
    }
  }

  output {
    traces = [otelcol.processor.batch.default.input]
  }
}
```

**How it works**

- Tail sampling buffers every span of a trace in memory as it arrives. The decision about whether to keep or drop the trace is deferred until either the root span is received or `decision_wait` (10s here) elapses, whichever comes first. That delay is what lets the sampler see the full picture (status codes, attributes, latency) before committing.
- Policies are evaluated with OR logic: if **any** policy votes to sample, the whole trace is kept. That's why the two policies in this config compose naturally:
  - `type = "status_code"` with `status_codes = ["ERROR"]` retains every trace that contains at least one error span. Each dead-drop fragment the field agent is leaking rides on an error span, so this policy guarantees every fragment survives.
  - `type = "probabilistic"` with `sampling_percentage = 5.0` keeps 5% of healthy traffic, preserving a baseline for general observability.
- Swapping head sampling for tail sampling is exactly what unlocks the mission: under head sampling, error traces had the same 5% survival odds as anything else, so most fragments were dropped before anyone could read them. Under tail sampling, the `status_code` policy makes error traces deterministic keepers.
- Make sure `otelcol.receiver.otlp.default.output.traces` points at `otelcol.processor.tail_sampling.mission4.input`, and remove or rewire around the `probabilistic_sampler` from Mission III so traces do not flow through both.

> [!IMPORTANT]
> **Tail sampling is more involved to operate than head sampling.** The workshop runs a single Alloy instance so this is handled for you, but in a real deployment there are two operational constraints to plan for:
>
> 1. **Memory:** every span is buffered until `decision_wait` expires or the root span arrives, so the collector needs enough memory to hold `decision_wait` worth of in-flight traces.
> 2. **Trace locality:** all spans belonging to the same trace must reach the same Alloy instance, otherwise the sampler only sees part of the trace and cannot make an informed decision. Two common ways to guarantee this:
>    - A load balancer in front of Alloy that does consistent hashing on the trace ID, so every span for a given trace lands on the same instance.
>    - The [`otelcol.exporter.loadbalancing`](https://grafana.com/docs/alloy/latest/reference/components/otelcol/otelcol.exporter.loadbalancing/) component, which routes spans to downstream Alloy instances by trace ID.
>
> For a fuller walkthrough of both sampling strategies and how to lay them out in a real deployment, see [Sampling with the OpenTelemetry Collector](https://grafana.com/docs/opentelemetry/collector/sampling/).

</details>

### Verify Your Work

```bash
make mission4-verify
```

## All Commands

| Command | Description |
|---------|-------------|
| **Environment** | |
| `make start` | Start all services |
| `make stop` | Stop all services and clean volumes |
| `make restart` | Restart everything |
| `make clean` | Full cleanup including logs |
| **Config** | |
| `make alloy-reload` | Reload Alloy config after changes |
| **Monitoring** | |
| `make logs` | Tail mission-control logs |
| `make alloy-logs` | Tail Alloy logs |
| `make metrics` | View metrics endpoint |
| `make status` | Check mission status |
| **Missions** | |
| `make mission1` / `mission2` / `mission3` / `mission4` | Activate a mission |
| `make mission1-verify` / `mission2-verify` / `mission3-verify` / `mission4-verify` | Verify a mission solution |
| `make reset` | Reset all missions |
| **Mission IV Endgame** | |
| `make access-token` | Check token fragment recovery (wait ~75s) |
| `make deaddrop KEY="..."` | Unlock the dead drop with your assembled token |

## Troubleshooting

> [!CAUTION]
> **`illegal character U+201C`**
> This means you have “smart quotes” (curly quotes) in your config, likely from copying text via a browser or rich-text editor. Replace all `“` and `”` with plain ASCII double quotes (`”`).

- **Alloy not receiving traces?**
  Run `make alloy-logs` to check for connection errors.
- **Port conflicts?**
  Check ports 8080, 3000, 3100, 3200, 4317, 4318, 9009, 12347.
- **`scrape_timeout greater than scrape_interval`?**
  Add `scrape_timeout = "4s"` to your `prometheus.scrape` block (or any value less than `scrape_interval`).
- **Mission 2: `NoSuchBucket`?**
  The S3 init container may have failed on startup. Recreate the bucket manually:
  ```bash
  docker compose exec localstack curl -X PUT http://localhost:4566/audit-logs
  ```
