
%% create bucket %%
aws s3 mb [bucketname]

%%  upload a couple of objects to the buckets %%
aws s3 cp file.txt [bucketname]