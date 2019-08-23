# nextflow_issue
Simple nextflow pipeline, generateb by flowcraft, for testing purposes

### Why
Since [nextlow's]() latest release, [flowcraft] generated pipelines stopped working (see ).  I traced the error to the `nxf_container_env()` in the `.command.run` file. All flowcraft generated pipelines use the same [nextflow.config](https://raw.githubusercontent.com/assemblerflow/flowcraft/master/flowcraft/generator/templates/nextflow.config) file, that includes the env scope. 
For some reason, the paths defined there show up with escaped quotes. 

```nxf_container_env() {
cat << EOF
export PYTHONPATH=\"\$baseDir/templates:\$PYTHONPATH\"
export PATH=\"/home/ines/temp/flowcraft_test/v19/bin:\$baseDir/templates:\$PATH\"
EOF
}
```

For testing purposes, I've created this repository. No test data in included in this repository. 


### Run the pipeline

This pipeline expects paired-end data. To run, paste the following command on your terminal:
`nextlow run main.nf --fastq "/path/to/fastq/*_{1,2}*"`
Bu default, it runs with singularity. It can be altered to docker by providing the `-profile docker`. 

