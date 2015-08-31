#hdf5

## Libs
- [pydap](http://www.pydap.org) Pydap is a pure Python library implementing the Data Access Protocol, also known as DODS or OPeNDAP. You can use Pydap as a client to access hundreds of scientific datasets in a transparent and efficient way through the internet; or as a server to easily distribute your data from a variety of formats.

## Apps / Tools

- h5ls: command line tool
	- h5ls -vlr xx.hdf5: print verbose recursive info
- h5dump: more verbose command line info dumping 	 
- [hfserve](h5serv) python hdf5 restful server. I think there is a h5pyd client too.
- [HDF Compass](https://www.hdfgroup.org/projects/compass/)- nice hdd viewer (written in python by hdd group)
- [ViTables](http://vitables.org) Python hdf viewer / editor.


## Opening files

Open file but fail if it exists to prevent overwrite. Best to always wrap in a context manager.

    with h5py.File(" name.hdf5", "w-") as f:

