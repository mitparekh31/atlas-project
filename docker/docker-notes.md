# Docker Learning Notes

# what is Docker layer?
# -> A Docker layer is a read-only filesystem layer created during the image build process. Most Dockerfile instructions create a new layer. Docker combines these layers to create the final Docker image.

# what is Docker cache?
# -> Docker cache stores previously built image layers. If an instruction and its inputs have not changed, Docker reuses the cached layer instead of rebuilding it. This makes image builds much faster. 

# Why is package.json copied first ?
# -> The package.json file contains the project's dependencies. Docker copies it before the application source code so that the npm install layer can be cached. If only the application code changes, Docker reuses the cached dependency layer, which speeds up future builds.

# Difference between RUN and CMD.
# -> RUN executes commands while building the Docker image. The result becomes part of the image.
# CMD defines the default command that runs when a container starts. It is executed only after docker run.

# What happens during docker build?
# -> When docker build is executed:

# 1. Docker reads the Dockerfile.
# 2. It downloads the base image if it is not available locally.
# 3. Docker executes each instruction one by one.
# 4. After each instruction, Docker creates a new layer.
# 5. Docker checks whether a cached layer can be reused.
# 6. Finally, all layers are combined to create the Docker image.
