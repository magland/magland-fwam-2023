---
marp: true
paginate: true
theme: magland-theme
header: <img src="https://user-images.githubusercontent.com/3679296/276917690-ed331783-4853-44ea-969f-b29d9415d21d.png" style="margin-left:15px" width="200px" />
footer: <div>Figurl FWAM 2023</div>
---

<!-- For using custom theme, see https://github.com/orgs/marp-team/discussions/115 -->

# Collaborative scientific visualization in the browser with Figurl

Jeremy Magland and Jeff Soules, Center for Computational Mathematics, Flatiron Institute

Flatiron-Wide Autumn Meeting (FWAM), October 2023

<br />
<br />

<center>
<img src="https://github.com/flatironinstitute/figurl/raw/main/figurl.png" width="20%" />
<br />
Follow along: <a href="https://github.com/magland" target="_blank">https://github.com/magland</a>
</center>

---

## Visualization in the scientific process

![bg right:20% 40%](https://upload.wikimedia.org/wikipedia/commons/5/55/Magnifying_glass_icon.svg)

Visualization is critical at every stage of the data-centric scientific process

- Data exploration
- Quality control
- Curation
- Analysis and interpretation
- Communication

---

## Benefits of interactive visualizations

![bg right:45% 100%](https://user-images.githubusercontent.com/3679296/276534849-9c3fbc26-b3a9-4b9a-a423-05a277bad208.png)

![bg right:40% 80%](https://user-images.githubusercontent.com/3679296/275474172-b9a86083-9815-4bd5-a735-11b17142e9f0.png)

Compared with static plots, interactive visualizations enable:

- Exploration of large, complex datasets
- Exploration of parameter space
- Gain intuition about dataset
- Identification of outliers and artifacts (QC)
- Interactive / collaborative curation

---

## Current limitations in sharing interactive visualizations

![bg right:30% 60%](https://user-images.githubusercontent.com/3679296/275475112-037b1d15-8342-4234-ab16-6e07aee54ebe.png)

Interactive visualizations are not easily shared as they often require:

- Specific operating system / hardware
- Specialized software
- Transfer of large datasets
- Expertise in setting up / reproducing the visualization

---

## Why web-based software?

![bg right:30% 80%](https://live.staticflickr.com/8364/8270409318_bdd1115652_w.jpg)

- Easy to use
- Easy to share
- Cross-platform
- Development cycle advantages (simplifies distribution, etc.)
- Integrates naturally with cloud resources
- Collaboration
- Reproducibility
* **Limitations:** no native access to local files/software, requires internet connection, limited access to previous versions, requires coding in JavaScript

---

## Existing browser-based visualization tools

[Observable](https://observablehq.com), [Vega](https://vega.github.io/vega/), [Plotly](https://plotly.com/), [Bokeh](https://bokeh.org/), [D3](https://d3js.org/), [Matplotlib](https://matplotlib.org/stable/index.html), [Google Charts](https://developers.google.com/chart), [VisPy](https://vispy.org/), [Altair](https://altair-viz.github.io/), [Deck.gl](https://deck.gl/), [P5.js](https://p5js.org/), [Three.js](https://threejs.org/), [Babylon.js](https://www.babylonjs.com/), [A-Frame](https://aframe.io/), [Pixi.js](https://www.pixijs.com/), [Recharts](https://recharts.org/en-US/), [NVD3](http://nvd3.org/), [C3.js](https://c3js.org/), [Chart.js](https://www.chartjs.org/), [Vega-Lite](https://vega.github.io/vega-lite/), [ECharts](https://echarts.apache.org/en/index.html), [Highcharts](https://www.highcharts.com/), [Leaflet](https://leafletjs.com/)

###  ... and many more

These are powerful tools, but they typically need to be embedded in a framework to be usable and shareable.

---

## Executable notebooks (browser-based solution)

![bg right:50% 90%](https://github.com/magland/magland-fwam-2023/assets/3679296/e83cfb54-12a5-49e9-a92f-ec1a1e8dd5a8)

- Jupyter, Google Colab, etc.
- **Pros**: reproducible, self-documenting, interactive
- Shareable on github, but only for static rendering of output cells
- There are other systems for rendering interactive outputs, but they have limitations
- **Cons**: Requires a running backend, Cluttered by code, etc.

---

## Binder: Making notebooks shareable

![bg right:40% 100%](https://user-images.githubusercontent.com/3679296/275518924-00572b53-d099-457d-90ec-d8fb1c1a4eac.png)

- Enable anyone to run code from public repositories.
- Allow authors to create interactive versions of their code.
- Scale to handle many users at once.

---

## Binder: How it works

- **Git Repository**: Start with code/notebooks in a git repo (e.g., GitHub)
- **Dependencies**: (requirements.txt or environment.yml)
- **Docker Image**: Converts repo into Docker image
- **Launch Instance**: Starts instance of that image
- **Interactive Sessions**: Jupyer notebooks
- **Ephemeral**: Changes during session are ephemeral; lost when session ends.

---

## Binder: Limitations

- Requires running backend.
    - Depending on number of users/views, can be expensive
    - Infrastructure maintenance
- User needs to wait for the backend to start
    - Matplotlib demo: https://matplotlib.org/ (relatively fast example 30-90 sec)
    - If image is large or needs to be built, can take several minutes

- Binder links can break over time
    - [The first Google hit for a live binder is broken](https://elifesciences.org/labs/8653a61d/introducing-binder-2-0-share-your-interactive-research-environment) (pandas installation error)
    - Could rely on external content or services that change over time

---

## Binder: Can be very slow to load

![bg right:50% 90%](https://user-images.githubusercontent.com/3679296/276528807-9a64e584-844a-4ccc-ac41-401ce6563af1.png)

Here's a powerful example but very slow to load because image needs to be built at startup. (From my experience these often ultimately fail to load.)

<br />

https://pythoninchemistry.org/sim_and_scat/classical_methods/van_der_waals

---

## Observable (observablehq.com)

![bg right:45% 85%](https://user-images.githubusercontent.com/3679296/275536901-be42678b-2acc-4ea7-8232-1c9d5db20d45.png)

- **Interactive Exploration**: Users play with data and code
- **Collaboration**: Work with others in real-time
- **Reactivity**: Changes propagate automatically
- **Reproducibility**: Ensures results can be reproduced by others
- **Sharing and Publishing**: Disseminate findings easily

Example: <a href="https://observablehq.com/@redblobgames/centroid-and-voronoi-polygons" target="_blank">centroid-and-voronoi-polygons</a>

---

## Observable: Limitations

![bg right:50% 90%](https://user-images.githubusercontent.com/3679296/275540199-b8981686-c66a-4fce-a5db-e3c5d5469ee3.png)

- Uses modified JavaScript (main limitation)
- Performance issues for large datasets
- Visualizations must be embedded in notebooks

---

## Clickable hyperlink approach

![bg right:50% 90%](https://i0.wp.com/blog.eyewire.org/wp-content/uploads/2017/10/example_bundle_pyramidal.png?w=666&ssl=1)

- Example: [Neuroglancer](https://github.com/google/neuroglancer) (from Google)
- Dissemination using URLs
- No backend server required (client-side computation)
- [Open viewer](https://neuroglancer-demo.appspot.com/#!{'layers':{'image':{'type':'image'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/image'}_'ground-truth':{'type':'segmentation'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/ground_truth'_'segments':['21894'_'22060'_'158571'_'24436'_'2515']}}_'navigation':{'pose':{'position':{'voxelSize':[8_8_8]_'voxelCoordinates':[2914.500732421875_3088.243408203125_4045]}}_'zoomFactor':30.09748283999932}_'perspectiveOrientation':[0.3143535554409027_0.8142156600952148_0.4843369424343109_-0.06040262430906296]_'perspectiveZoom':443.63404517712684_'showSlices':false})


---

## Example Neuroglancer URL

<!-- ![bg right:40% 90%](https://github.com/magland/magland-fwam-2023/assets/3679296/02d77daf-ccf9-458f-9feb-724905769690) -->


`https://neuroglancer-demo.appspot.com/#!{'layers':{'image':{'type':'image'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/image'}_'ground-truth':{'type':'segmentation'_'source':'precomputed://gs://neuroglancer-public-data/flyem_fib-25/ground_truth'_'segments':['21894'_'22060'_'158571'_'24436'_'2515']}}_'navigation':{'pose':{'position':{'voxelSize':[8_8_8]_'voxelCoordinates':[2914.500732421875_3088.243408203125_4045]}}_'zoomFactor':30.09748283999932}_'perspectiveOrientation':[0.3143535554409027_0.8142156600952148_0.4843369424343109_-0.06040262430906296]_'perspectiveZoom':443.63404517712684_'showSlices':false}`

---

## Neuroglancer: Limitations

![bg right:50% 90%](https://user-images.githubusercontent.com/3679296/275907049-47a1fb7b-acad-49c7-a084-1aab86473c7d.png)

- This is a specialized tool
- Requires data be prepared and uploaded to a cloud bucket (expertise and special configuration)


---

## Figurl: overview

![bg right:35% 80%](https://user-images.githubusercontent.com/3679296/269425776-52d0eec8-35b4-40be-b5f1-44937265ba77.png)

- Simplifies sharing of interactive figures
    - Run Python script to generate shareable URL
    - Clickable hyperlink method
    - No backend server
    - Fast loading, not embedded in notebook
- Create custom visualization plugins
    - Static HTML bundles in the cloud
    - React/typescript (or other frameworks)
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
```

https://figurl.org/f?v=gs://figurl/plotly-1&d=sha1://5c6ec276ce9a3b20b208aaff911b037ce4052e51&label=plotly%20example%20-%20iris%203d

---

## Figurl: Embedding in presentations / websites

<table><tbody><tr>
<td>
<iframe src="https://figurl.org/f?v=gs://figurl/plotly-1&d=sha1://5c6ec276ce9a3b20b208aaff911b037ce4052e51&label=plotly%20example%20-%20iris%203d&hide=1
" width="500px" height="400px"></iframe>
</td>
<td>
<iframe src="https://figurl.org/f?v=gs://figurl/figneuro-1&d=sha1://e0b6c94ca7e6d0ef761e94f3551c00eb8ed23636&label=Spike%20amplitudes%20example&hide=1
" width="500px" height="400px"></iframe>
</td>
</tr></tbody></table>

---

## Figurl architecture

<img src="https://user-images.githubusercontent.com/3679296/269635248-6f9ee2b9-3217-4a8b-8338-a7535851a8a3.svg" />


---

## Figurl Neurophysiology Example ([figurl](https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://8d61e59b2806cf927ca1bd265923c23f5c37b990&label=experiment1_Record%20Node%20104%23Neuropix-PXI-100.ProbeA-AP_recording1%20-%20kilosort2_5%20-%20Sorting%20Summary))

<img src="https://user-images.githubusercontent.com/3679296/271270920-8f10b747-bac7-4664-b8fd-bb6cd5867d18.svg" height="95%" width="95%" />

---

## Figurl Neurophysiology Example

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

https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://8d61e59b2806cf927ca1bd265923c23f5c37b990&label=experiment1_Record%20Node%20104%23Neuropix-PXI-100.ProbeA-AP_recording1%20-%20kilosort2_5%20-%20Sorting%20Summary

---

## Figurl Timeseries Graph Example

```python
import numpy as np
import sortingview.views as vv

G = vv.TimeseriesGraph(
    legend_opts={'location': 'northwest'},
    y_range=[-15, 15], hide_x_gridlines=False, hide_y_gridlines=True
)
n1 = 5000
t = np.arange(0, n1) / n1 * 10; v = t * np.cos((2 * t)**2)
G.add_line_series(name='blue line', t=t, y=v.astype(np.float32), color='blue')
n2 = 400
t = np.arange(0, n2) / n2 * 10; v = t * np.cos((2 * t)**2)
G.add_marker_series(name='red marker', t=t, y=v.astype(np.float32), color='red', radius=4)
v = t + 1
G.add_line_series(name='green dash', t=t, y=v.astype(np.float32), color='green', width=5, dash=[12, 8])
t = np.arange(0, 12) / 12 * 10; v = -t - 1
G.add_marker_series(name='black marker', t=t, y=v.astype(np.float32), color='black', radius=8, shape='square')

print(G.url(label='TimeseriesGraph-Example'))
```

https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://e6ca2d115aa3b92b6da77643f07349cb8f9b5546&label=TimeseriesGraph-Example

---

## Anatomy of a Figurl URL

<img src="https://user-images.githubusercontent.com/3679296/276540186-a06a7043-1130-4f84-bdea-3b4bfcfb28be.png" />

---

## Figurl Altair Example

```python
import figurl as fig

# From: https://altair-viz.github.io/gallery/simple_histogram.html
import altair as alt
from vega_datasets import data

source = data.movies.url

chart = alt.Chart(source).mark_bar().encode(alt.X("IMDB_Rating:Q", bin=True), y='count()')

# Create and print the figURL
url = fig.Altair(chart).url(label='example altair chart')
print(url)
```

https://figurl.org/f?v=gs://figurl/vegalite-2&d=sha1://f5920cbea57e42211f7cf83065230132713a3f01&label=example%20altair%20chart

---

## Figurl 3D Surface Example

```python
vtk_uri = 'sha1://e54d59b5f12d226fdfe8a0de7d66a3efd1b83d69?label=rbc_001.vtk'
vtk_path = kcl.load_file(vtk_uri)

vertices, faces = vv._parse_vtk_unstructured_grid(vtk_path)

W = vv.Workspace()
S = W.add_surface(name='red-blood-cell', vertices=vertices, faces=faces)
W.add_surface_scalar_field(name='scalarX', surface=S, data=vertices[:, 0])
W.add_surface_scalar_field(name='scalarY', surface=S, data=vertices[:, 1])
W.add_surface_scalar_field(name='scalarZ', surface=S, data=vertices[:, 2])

F = W.create_figure()
url = F.url(label='rbc_surface_scalar_fields')
print(url)
```
https://figurl.org/f?v=gs://figurl/volumeview-4&d=sha1://5a9cc08b0d8ce7a71c132b41bb5f88b9247568ba&label=rbc_surface_scalar_fields

---

## 3D surface

<iframe src="https://figurl.org/f?v=gs://figurl/volumeview-4&d=sha1://5a9cc08b0d8ce7a71c132b41bb5f88b9247568ba&label=rbc_surface_scalar_fields&hide=1" width="1100px" height="500px"></iframe>

---

## Figurl uses Kachery

![bg right:50% 100%](https://user-images.githubusercontent.com/3679296/271279738-995996c6-a545-4cf7-9f5d-5473ca302547.png)

Content Addressable Storage (CAS) database in the cloud
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

---

## [Figurl gallery](https://magland.github.io/figurl-gallery-viewer/)

<image src="https://user-images.githubusercontent.com/3679296/271276312-886a4aec-f972-4d9c-a821-19a2ae3d0de2.png" width="95%" />


---

## [Figurl gallery](https://magland.github.io/figurl-gallery-viewer/)

<image src="https://user-images.githubusercontent.com/3679296/271276944-449ddb6a-d640-48b2-9ee3-655ecb82e2fd.png" width="95%" />

---

## [Figurl gallery](https://magland.github.io/figurl-gallery-viewer/)

<image src="https://user-images.githubusercontent.com/3679296/271277359-9622d633-c375-467c-9549-3a69ca1616d9.png" width="95%" />

---

## Lab-specific visualization plugins (Loren Frank Lab)

<center>
<img src="https://user-images.githubusercontent.com/3679296/276545564-84b529e7-5125-4169-8612-a662b63bbfb1.png" width="850px" />
</center>

---

## Lab-specific visualization plugins (with Ralph Peterson)

<center>
<img src="https://user-images.githubusercontent.com/3679296/276546096-1ccda771-0a5e-47c3-93bd-df29dc86744f.png" width="850px" />
</center>

---

## Live example ([link](https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://ac58ec4039b5ac24054260be7c8caa7d909bb0cb&label=alison%27s%20example)) (Loren Frank Lab)

<iframe src="https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://ac58ec4039b5ac24054260be7c8caa7d909bb0cb&label=alison%27s%20example&hide=1" width="1100px" height="500px"></iframe>

---

## Live example ([link](https://figurl.org/f?v=https://scratchrealm.github.io/skeleton-pose-annotator/v1&d=sha1://272f16546785718bf2fa1d43f21019b5b24f5cad&s={%22annotation%22:%22gh://scratchrealm/example-annotations/main/spa/example1.json%22}&label=example%20labeling%20stack)) (SLEAP-type interface)

<iframe src="https://figurl.org/f?v=https://scratchrealm.github.io/skeleton-pose-annotator/v1&d=sha1://272f16546785718bf2fa1d43f21019b5b24f5cad&s={%22annotation%22:%22gh://scratchrealm/example-annotations/main/spa/example1.json%22}&label=example%20labeling%20stack&hide=1" width="1100px" height="500px"></iframe>

---

## Live example ([link](https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://43eb8efe806c5341225d789b8f447a88cde56d15&label=2d%20decode%20composite&zone=franklab.default)) (Loren Frank Lab)

<iframe src="https://figurl.org/f?v=gs://figurl/spikesortingview-10&d=sha1://43eb8efe806c5341225d789b8f447a88cde56d15&label=2d%20decode%20composite&zone=franklab.default&hide=1" width="1100px" height="500px"></iframe>

---

## Live example ([link](https://figurl.org/f?v=gs://figurl/figneuro-1&d=sha1://73ba63a0ab552f9d124bc5b6a09254c822576fa0&label=audio/video/spikes%20composite%20view)) (with Ralph Peterson)

<iframe src="https://figurl.org/f?v=gs://figurl/figneuro-1&d=sha1://73ba63a0ab552f9d124bc5b6a09254c822576fa0&label=audio/video/spikes%20composite%20view&hide=1" width="1100px" height="500px"></iframe>

---

## Advanced: Embedding Figurl Figures in Markdown Documents

![bg right:50% 80%](https://user-images.githubusercontent.com/3679296/275901510-d12adf57-82f6-4631-b0f3-aad81506b996.png)

https://github.com/dcmnts/isosplit-paper/blob/main/isosplit.md

yields

https://doc.figurl.org/gh/dcmnts/isosplit-paper/blob/main/isosplit.md

---

## Summary

- Many powerful visualization tools exist, but frictionless sharing is still a challenge
- Figurl is an open-source browser-based visualization tool
    - Uses the clickable hyperlink method
    - Reduces friction for sharing interactive visualizations
    - Promotes scientific collaboration

---

## Future directions

- Develop additional visualization plugins
- Expand collaborations and attract developers
- Improve kachery infrastructure

---

## Thank you!

- Flatiron: Jeff Soules
- Frank lab: Loren Frank, Eric Denovellis, Kyu Hyun Lee, Alison Comrie, Michael Coulter
- Allen Institute: Alessio Buccino

<br />

https://github.com/flatironinstitute/figurl
https://github.com/flatironinstitute/kachery-cloud