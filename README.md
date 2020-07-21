# rd-sgoab-datasets
Datasets for the Saint George on a Bike project

## Object detection dataset

Dataset for detecting objects in paintings. All the data has been harvested using the [python wrapper](https://github.com/europeana/rd-europeana-python-api/tree/master/europeana) for Europeana's Search API . 

The field reusability was set to open, so all images collected are of public use. 

The queries have been obtained from the [list of classes](https://docs.google.com/spreadsheets/d/12dAgM4DKX-y6UH4TVF_Q_DjAd4kNz_2g0qIyleQqmAM/edit#gid=0) and translated to other languages for matching a greater number of results

[Example Multilingual Harvesting](https://colab.research.google.com/drive/1gTBo32a3RPWDhLbVwIh1gFqoFrlvXMAB?usp=sharing) 

Annotated with the [VGG annotation tool](http://www.robots.ox.ac.uk/~vgg/software/via/via.html). The dataset can be loaded and visualized with this tool.

### Instructions

Clone the repository

```
git clone https://github.com/europeana/rd-sgoab-datasets.git
cd rd-sgoab-datasets

```


```

import json

with open('SGoaB_object_det_359_annotated_254.json') as f:
  d = json.load(f)

data_dict = d['_via_img_metadata']
url_list = list(data_dict.keys())
for url in url_list[:5]:
  print('{}'.format(url))
  regions = data_dict[url]['regions']
  for r in regions:
    cat = r['region_attributes']['class'].replace('\n','').strip()
    x1 = r['shape_attributes']['x']
    y1 = r['shape_attributes']['y']
    x2 = x1+r['shape_attributes']['width']
    y2 = y1+r['shape_attributes']['height']
    print('Category: {}   bbox: {}'.format(cat,[x1,x2,y1,y2]))
  print('\n')
```






