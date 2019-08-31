
#first we have to import 7 libraries
#we could have used a single library but to make a good url shrotener,
#we need to improt 7 lib



from _future_ import with_statement
import contextlib

try:
    from urllib.parse import urlencode
except ImportError:
    from urllib import urlencode
try:
    from urllib.request import urlopen
except ImportError:
    from urllib2 import urlopen

import sys




#here we have encoded the url and appended or added that url to the api
#we open request_url using urlopen
#then the response is converted to UTF-8 since urlopen() returns a stream of bytes rather than a string

def make_tiny(url):
    request_url= ('http://tinyurl.com/api-create.php?' + urlencode({'url':url}))
    with contextlib.closing(urlopen(request_url)) as response:
        return response.read().decode('utf-8')

def main(): 
         for tinyurl in map(make_tiny,sys.argv[1:]):
                    print(tinyurl)
         



#then we called main and will take userI/P using sys.argv.
#we can put as many urls we want to shorten
#tiny.map() is a simple way of looping over a list and passing it to a function 1by1

if _name_ =='_main_':
         main()
