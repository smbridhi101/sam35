
#!/usr/bin/py
from PIL import Image
import os, shutil

for root, dirs, files in os.walk(".", topdown=False):
 for name in files:
  try:
   path = os.path.join(root, name)
   im = Image.open(path)
   width,height=im.size
   if width<1024 and height<768:
    print(name,'  ', path , im.format,"%dx%d" % im.size)
    shutil.copy2(path,'../Matched/')
  except IOError:
   pass
