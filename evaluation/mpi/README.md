## Open-MPI
### To install Open-MPI:
visit:\
https://www.open-mpi.org/software/ompi/v4.1/

### To run the MPI jobs with slurm
The shell script was utilized to exchange messages between 2 nodes in the cluster, utilizing RDMA. The maximum message size was set to 16M.
For more information about running Open-MPI with slurm, visit: \
https://docs.open-mpi.org/en/v5.0.0rc9/running-apps/slurm.html 

The experiments show how the change of threshold value changes the amount of RDMA Read and RDMA Send packets used for communication:
- Setting the UCX Rendezvous Threshold to 1M
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/MPI_1M.png?raw=true)
- Setting the UCX Rendezvous Threshold to 20M
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/MPI_20M.png?raw=true)
