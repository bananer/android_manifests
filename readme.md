```sh
git -C /root/lineageos/local_manifests/ pull
```
```sh
docker run --interactive --tty --rm \
    -e "BRANCH_NAME=lineage-18.1" \
    -e "DEVICE_LIST=river,mako" \
    -e "INCLUDE_PROPRIETARY=false" \
    -e "LOCAL_MIRROR=false" \
    -e "SIGNATURE_SPOOFING=yes" \
    -e "SIGN_BUILDS=true" \
    -e "CLEAN_AFTER_BUILD=false" \
    -e "CCACHE_SIZE=50G" \
    -e "RELEASE_TYPE=BANANER" \
    -e "OTA_URL=https://lineageos.nagler.world/api" \
    -e "ZIP_SUBDIR=false" \
    -e "CUSTOM_PACKAGES=GmsCore GsfProxy FakeStore MozillaNlpBackend NominatimNlpBackend com.google.android.maps FDroid FDroidPrivilegedExtension additional_repos.xml AuroraServices" \
    -v "lineageos_src:/srv/src" \
    -v "mainframe_lineageos_zips:/srv/zips" \
    -v "lineageos_logs:/srv/logs" \
    -v "lineageos_ccache:/srv/ccache" \
    -v "/root/lineageos/keys:/srv/keys" \
    -v "/root/lineageos/local_manifests:/srv/local_manifests:ro" \
    -v "/root/lineageos/userscripts:/srv/userscripts:ro" \
    --memory="14g" --cpus="3.7" \
    lineageos4microg/docker-lineage-cicd
```