---
marp: true
paginate: true
theme: magland-theme
footer: Magland FWAM 2023
---

<!-- For using custom theme, see https://github.com/orgs/marp-team/discussions/115 -->

## Collaborative scientific visualization in the browser with Figurl

Jeremy Magland, Center for Computational Mathematics, Flatiron Institute

### With

- Flatiron: Jeff Soules
- Frank lab: Loren Frank, Eric denovellis, Kyu Hyun Lee, Alison Comrie, Michael Coulter
- Other: Alessio Buccino

---

Include slides on observable and alternatives

---

## Role of visualization in the scientific process

![bg right:20% 40%](https://upload.wikimedia.org/wikipedia/commons/5/55/Magnifying_glass_icon.svg)

Visualization is critical at every stage of the data-centric scientific process

- Data exploration
- Data cleaning and quality control
- Analysis and interpretation
- Communication of results to scientific community

---

## Benefits of interactive visualizations

![bg right:40% 80%](https://user-images.githubusercontent.com/3679296/275474172-b9a86083-9815-4bd5-a735-11b17142e9f0.png)

Compared with static plots, interactive visualizations enable:

- Exploration of large, complex datasets
- Interactive exploration of parameter space
- Gain intuition about the data
- Rapid identification of outliers and artifacts
- Interactive hypothesis testing
    - e.g., "What if I remove this outlier?"
- Interactive curation of datasets

---

## Current limitations in sharing interactive visualizations

![bg right:30% 60%](https://user-images.githubusercontent.com/3679296/275475112-037b1d15-8342-4234-ab16-6e07aee54ebe.png)

Interactive visualizations are not easily shared as they often require:

- Specialized operating system / hardware
- Specialized software
- Transfer of large datasets
- Expertise in setting up / reproducing the visualization

---

## Why web-based software?

![bg right:30% 80%](https://live.staticflickr.com/8364/8270409318_bdd1115652_w.jpg)

- **Easy to use:** no installation
- **Easy to share:** copy-paste the link
- **Cross-platform:** all desktop options and mobile
- **Development cycle advantages:** simplifies distribution, etc.
- **Integrates naturally with cloud resources**
- **Collaboration**
- **Reproducibility**
* **Limitations:** no native access to local files/software, requires internet connection, limited access to previous versions, requires coding in JavaScript

---

## Existing browser-based visualization tools

[Observable](https://observablehq.com), [Vega](https://vega.github.io/vega/), [Plotly](https://plotly.com/), [Bokeh](https://bokeh.org/), [D3](https://d3js.org/), [Matplotlib](https://matplotlib.org/stable/index.html), [Google Charts](https://developers.google.com/chart), [VisPy](https://vispy.org/), [Altair](https://altair-viz.github.io/), [Deck.gl](https://deck.gl/), [Polymetric](https://polymetric.dev/), [P5.js](https://p5js.org/), [Three.js](https://threejs.org/), [Processing.js](http://processingjs.org/), [Babylon.js](https://www.babylonjs.com/), [Phaser](https://phaser.io/), [A-Frame](https://aframe.io/), [P5.js](https://p5js.org/), [Pixi.js](https://www.pixijs.com/), [Recharts](https://recharts.org/en-US/), [NVD3](http://nvd3.org/), [C3.js](https://c3js.org/), [D3.js](https://d3js.org/), [D3plus](https://d3plus.org/), [Chart.js](https://www.chartjs.org/), [Vega-Lite](https://vega.github.io/vega-lite/), [Vega](https://vega.github.io/vega/), [ECharts](https://echarts.apache.org/en/index.html), [Highcharts](https://www.highcharts.com/), [Leaflet](https://leafletjs.com/)

###  ... and many more

These are powerful tools, but they don't offer frictionless sharing of interactive visualizations out of the box.

---

## Executable notebooks (browser-based solution)

![bg right:50% 90%](https://github.com/magland/magland-fwam-2023/assets/3679296/e83cfb54-12a5-49e9-a92f-ec1a1e8dd5a8)

- Jupyter, Google Colab, etc.
- Pros: reproducible, self-documenting, interactive
- shareable, but only for static rendered notebooks
- Cons: Requires a running backend, Limited ability to share interactive visualizations, Cluttered by code, etc.

---

## Binder: Goals

![bg right:40% 100%](https://user-images.githubusercontent.com/3679296/275518924-00572b53-d099-457d-90ec-d8fb1c1a4eac.png)

- Enable anyone to run code from public repositories.
- Allow authors to create interactive versions of their code.
- Scale to handle many users at once.

---

## Binder: How it works

- **GitHub Repositories**: Starts with code/notebooks in a GitHub repo.
- **Dependencies**: Uses requirements.txt or environment.yml for environment setup.
- **Docker Image**: Binder converts the repo into a Docker container image.
- **Launch Instance**: When accessed, Binder starts an instance of that image.
- **Interactive Sessions**: Users can interact with notebooks, apps, or visualizations.
- **Ephemeral**:: All changes made during a session are ephemeral; they're lost when session ends.

---

## Binder: Limitations

- Requires a running backend.
    - Depending on number of users/views, this can be expensive.
    - Requires maintaining a running server.
- User needs to wait for the backend to start.
    - Matplotlib demo: https://matplotlib.org/ (took 80 sec for me)
    - If image is large or needs to be build, can tak several minutes

- Binder links can break over time
    - [The first Google hit for a live binder is broken](https://elifesciences.org/labs/8653a61d/introducing-binder-2-0-share-your-interactive-research-environment) (pandas installation error)
    - Could rely on external content or services that change over time.

---

## Observable: Goals

![bg right:50% 85%](https://user-images.githubusercontent.com/3679296/275536901-be42678b-2acc-4ea7-8232-1c9d5db20d45.png)

- **Interactive Exploration**: Allows users to play with data and code.
- **Collaboration**: Share and work with others in real-time.
- **Reactivity**: Changes propagate automatically.
- **Reproducibility**: Ensure results can be reproduced by others.
- **Sharing and Publishing**: Disseminate findings easily.

---

## Observable: Limitations

![bg right:50% 90%](https://user-images.githubusercontent.com/3679296/275540199-b8981686-c66a-4fce-a5db-e3c5d5469ee3.png)

- Uses modified JavaScript (this is the main limitation)
- Performance issues for large datasets
- Visualizations must be embedded in notebooks

---

## Clickable hyperlink approach

![bg right:50% 90%](https://i0.wp.com/blog.eyewire.org/wp-content/uploads/2017/10/example_bundle_pyramidal.png?w=666&ssl=1)

- Example: [Neuroglancer](https://github.com/google/neuroglancer)
- Dissemination using URLs
- No backend server required (client-side computation)
- [Open viewer](https://neuroglancer-demo.appspot.com/#!{'layers':{'image':{'type':'image'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/image'}_'ground-truth':{'type':'segmentation'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/ground_truth'_'segments':['21894'_'22060'_'158571'_'24436'_'2515']}}_'navigation':{'pose':{'position':{'voxelSize':[8_8_8]_'voxelCoordinates':[2914.500732421875_3088.243408203125_4045]}}_'zoomFactor':30.09748283999932}_'perspectiveOrientation':[0.3143535554409027_0.8142156600952148_0.4843369424343109_-0.06040262430906296]_'perspectiveZoom':443.63404517712684_'showSlices':false})


---

## Example Neuroglancer URL

![bg right:25% 90%](https://github.com/magland/magland-fwam-2023/assets/3679296/02d77daf-ccf9-458f-9feb-724905769690)

`https://neuroglancer-demo.appspot.com/#!{'layers':{'image':{'type':'image'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/image'}_'ground-truth':{'type':'segmentation'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/ground_truth'_'segments':['21894'_'22060'_'158571'_'24436'_'2515']}}_'navigation':{'pose':{'position':{'voxelSize':[8_8_8]_'voxelCoordinates':[2914.500732421875_3088.243408203125_4045]}}_'zoomFactor':30.09748283999932}_'perspectiveOrientation':[0.3143535554409027_0.8142156600952148_0.4843369424343109_-0.06040262430906296]_'perspectiveZoom':443.63404517712684_'showSlices':false}`

---

## Neuroglancer: Limitations

- This is a very specialized tool


---

## Figurl: overview

![bg right:25% 80%](https://user-images.githubusercontent.com/3679296/269425776-52d0eec8-35b4-40be-b5f1-44937265ba77.png)

- Simplifies sharing of interactive figures
    - Run a Python script to generate a shareable URL
    - Uses clickable hyperlink method of sharing
    - No backend server required
    - Fast loading, not embedded in notebook
- Create custom visualization plugins
    - Static HTML bundles in the cloud
    - React/typescript
- Promotes scientific collaboration, communication, reproducibility

---

## Figurl: Plotly example

![bg right:35% 90%](https://github.com/magland/magland-fwam-2023/assets/3679296/e9b8a289-f91e-4902-ac6a-c00d2d7d5ad4)

```python
import plotly.express as px
import figurl as fig

# Load the iris dataset and create a Plotly figure
iris = px.data.iris()
ff = px.scatter_3d(iris, x='sepal_length',
		y='sepal_width', z='petal_width',
		color='species')

# Create and print the figURL
url = fig.Plotly(ff).url(label='plotly example - iris 3d')
print(url)

# Output: 
# https://figurl.org/f?v=gs://figurl/plotly-1
# &d=sha1://5c6ec276ce9a3b20b208aaff911b037ce4052e51
# &label=plotly%20example%20-%20iris%203d
```

[Figurl link](https://figurl.org/f?v=gs://figurl/plotly-1&d=sha1://5c6ec276ce9a3b20b208aaff911b037ce4052e51&label=plotly%20example%20-%20iris%203d)

---

## Figurl architecture

![bg: 80%](https://user-images.githubusercontent.com/3679296/269635248-6f9ee2b9-3217-4a8b-8338-a7535851a8a3.svg)

---

## Figurl / SpikeInterface integration

```python
import spikeextractors as se

# Load the recording and sorting
recording, sorting = ...

# prepare SpikeInterface widget
widget = ...

# Prepare and print the figURL
url = widget.url(label='example')
print(url)
```

---

## Figurl / SpikeInterface integration ([figurl](https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://8d61e59b2806cf927ca1bd265923c23f5c37b990&label=experiment1_Record%20Node%20104%23Neuropix-PXI-100.ProbeA-AP_recording1%20-%20kilosort2_5%20-%20Sorting%20Summary))

<img src="https://user-images.githubusercontent.com/3679296/271270920-8f10b747-bac7-4664-b8fd-bb6cd5867d18.svg" height="95%" width="95%" />

---

## Figurl: Other examples - [gallery](https://magland.github.io/figurl-gallery-viewer/)

<image src="https://user-images.githubusercontent.com/3679296/271276312-886a4aec-f972-4d9c-a821-19a2ae3d0de2.png" width="95%" />


---

## Figurl: Other examples - [gallery](https://magland.github.io/figurl-gallery-viewer/)

<image src="https://user-images.githubusercontent.com/3679296/271276944-449ddb6a-d640-48b2-9ee3-655ecb82e2fd.png" width="95%" />

---

## Figurl: Other examples - [gallery](https://magland.github.io/figurl-gallery-viewer/)

<image src="https://user-images.githubusercontent.com/3679296/271277359-9622d633-c375-467c-9549-3a69ca1616d9.png" width="95%" />

---

## Figurl uses Kachery

![bg right:50% 100%](https://user-images.githubusercontent.com/3679296/271279738-995996c6-a545-4cf7-9f5d-5473ca302547.png)

Kachery is a Content Addressable Storage database in the cloud
- Minimal configuration for upload
- Download from anywhere
- Python client or Command-line client
- Serverless infrastructure
- Organized into zones (labs can host zones / pay for storage)

---

## Storing kachery data

```bash
echo "test-content" > test_content.txt
kachery-cloud-store test_content.txt
# output:
# sha1://b971c6ef19b1d70ae8f0feb989b106c319b36230?label=test_content.txt
```

From Python

```python
uri = kcl.store_text('example text', label='example.txt')
# uri = "sha1://d9e989f651cdd269d7f9bb8a215d024d8d283688?label=example.txt"
```

---

## Retrieving kachery data

```bash
kachery-cloud-load sha1://b971c6ef19b1d70ae8f0feb989b106c319b36230
```

```python
w = kcl.load_text('sha1://d9e989f651cdd269d7f9bb8a215d024d8d283688?label=example.txt')

x = kcl.load_json('sha1://d0d9555e376ff13a08c6d56072808e27ca32d54a?label=example.json')

y = kcl.load_npy("sha1://bb55205a2482c6db2ace544fc7d8397551110701?label=example.npy")

z = kcl.load_pkl("sha1://20d178d5a1264fc3267e38ca238c23f3e2dcd5d2?label=example.pkl")
```