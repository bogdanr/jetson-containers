# opencv_builder

<details open>
<summary><b>CONTAINERS</b></summary>
<br>

| **`opencv_builder`** | |
| :-- | :-- |
| &nbsp;&nbsp;&nbsp;Builds | [![`opencv_builder_jp51`](https://img.shields.io/github/actions/workflow/status/dusty-nv/jetson-containers/opencv_builder_jp51.yml?label=opencv_builder_jp51)](https://github.com/dusty-nv/jetson-containers/actions/workflows/opencv_builder_jp51.yml) [![`opencv_builder_jp46`](https://img.shields.io/github/actions/workflow/status/dusty-nv/jetson-containers/opencv_builder_jp46.yml?label=opencv_builder_jp46)](https://github.com/dusty-nv/jetson-containers/actions/workflows/opencv_builder_jp46.yml) |
| &nbsp;&nbsp;&nbsp;Requires | `L4T >=32.6` |
| &nbsp;&nbsp;&nbsp;Dependencies | [`build-essential`](/packages/build-essential) [`python`](/packages/python) [`cmake`](/packages/cmake/cmake_pip) |
| &nbsp;&nbsp;&nbsp;Dockerfile | [`Dockerfile`](Dockerfile) |

</details>

<details open>
<summary><b>RUN CONTAINER</b></summary>
<br>

To start the container, you can use the [`run.sh`](/run.sh)/[`autotag`](/autotag) helpers or manually put together a [`docker run`](https://docs.docker.com/engine/reference/commandline/run/) command:
```bash
# automatically pull or build a compatible container image
./run.sh $(./autotag opencv_builder)

# or if using 'docker run' (specify image and mounts/ect)
sudo docker run --runtime nvidia -it --rm --network=host opencv_builder:35.4.1

```
> <sup>[`run.sh`](/run.sh) forwards arguments to [`docker run`](https://docs.docker.com/engine/reference/commandline/run/) with some defaults added (like `--runtime nvidia`, mounts a `/data` cache, and detects devices)</sup><br>
> <sup>[`autotag`](/autotag) finds a container image that's compatible with your version of JetPack/L4T - either locally, pulled from a registry, or by building it.</sup>

To mount your own directories into the container, use the [`-v`](https://docs.docker.com/engine/reference/commandline/run/#volume) or [`--volume`](https://docs.docker.com/engine/reference/commandline/run/#volume) flags:
```bash
./run.sh -v /path/on/host:/path/in/container $(./autotag opencv_builder)
```
To launch the container running a command, as opposed to an interactive shell:
```bash
./run.sh $(./autotag opencv_builder) my_app --abc xyz
```
You can pass any options to `run.sh` that you would to [`docker run`](https://docs.docker.com/engine/reference/commandline/run/), and it'll print out the full command that it constructs before executing it.
</details>
<details open>
<summary><b>BUILD CONTAINER</b></summary>
<br>

If you use [`autotag`](/autotag) as shown above, it'll ask to build the container for you if needed.  To manually build it, first do this System Setup, then run:
```bash
./build.sh opencv_builder
```
The dependencies from above will be built into the container, and it'll be tested during.  See [`./build.sh --help`](/jetson_containers/build.py) for build options.
</details>