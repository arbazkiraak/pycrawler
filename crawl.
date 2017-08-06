import requests
from bs4 import BeautifulSoup

cookies = {
        'remember_user_token': '',
        'session': '',
        '_gid': 'GA1.2.2078484845.1501898960',
    }

headers = {
        'Accept-Encoding': 'gzip, deflate, br',
        'Accept-Language': 'en-US,en;q=0.8',
        'Upgrade-Insecure-Requests': '1',
        'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36',
        'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8',
        'Referer': 'https://www.site.com/users/confirmation/new?reconfirmation=true',
        'Connection': 'keep-alive',
        'Cache-Control': 'max-age=0',}

 
append_path=[] # Append all urls path 

with requests.Session() as s:
    req=s.get('https://www.site.com/dash', headers=headers, cookies=cookies)
    print str(req.status_code)+' '+str(req.url)
    
    with open('urls.txt') as f:
        for k in f.readlines():
            k = k.strip('\n')
            k = k.strip('\r')
            parsetest=s.get(k)
            print str(parsetest.status_code)+' '+str(parsetest.url)
            bf=BeautifulSoup(parsetest.text,'html.parser')
           # print 'Title : '+bf.title.string
            try:
                for i in bf('a'):
                    res=i.get('href')
                    if res.startswith('/'):
                        pathurl='https://www.site.com'+res
                        print pathurl
                        append_path.append(pathurl)
                    else:
                        pass
            except KeyboardInterrupt:
                pass
try:
    duplicates = list(set(append_path)) # Removes Duplicates
    with open('outputall_subs.txt','w') as f: # Save it
        for i in duplicates:
            f.write(str(i)+'\n')
            f.close()
            print "\n~!APPENDED!~\n"
except Exception as e:
    print e
    pass
    
