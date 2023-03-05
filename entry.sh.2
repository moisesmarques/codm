#!/bin/bash

#set -e
nvidia-smi

# variables to be passed as parameters
BUCKET=$4
COLLECT=$5
OUTPUT=$6

echo "processing collect '$COLLECT' from bucket $BUCKET to $OUTPUT"

cd /local

mkdir -p /local/images

aws s3 sync s3://$BUCKET/$COLLECT/ /local/images --no-progress

aws s3 cp s3://$BUCKET/settings.yaml .

# try using an overriden settings file
aws s3 cp s3://$BUCKET/$COLLECT/settings.yaml .  || true

# # try copying a boundary
# aws s3 cp s3://$BUCKET/$COLLECT/boundary.json .  || true

# BOUNDARY="--auto-boundary"

# if test -f "boundary.json"; then
#     BOUNDARY="--boundary boundary.json"
# fi

docker run --rm -v /local:/local --gpus all opendronemap/odm:gpu --project-path /local .

# copy ODM products
PRODUCTS=$(ls -d odm_* 3d_tile*)
for val in $PRODUCTS;
do
    aws s3 sync $val s3://$BUCKET/$COLLECT/$OUTPUT/$val --no-progress
done

# copy the log
aws s3 cp odm_$COLLECT-process.log s3://$BUCKET/$COLLECT/$OUTPUT/odm_$COLLECT-process.log

# try to copy the EPT data (it isn't named odm_*)
aws s3 sync entwine_pointcloud s3://$BUCKET/$COLLECT/$OUTPUT/entwine_pointcloud --no-progress  || exit 0
