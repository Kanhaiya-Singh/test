# test

NXE2OfD4KtGD4tUrxc6bHn5oW/m2ofVrXD+18RbvEoy0b5YZkngE9Zp5tfWKMIi4zTV8lsXSL/bX13gi1Knu/utq05eXnp6SyNukoSA6tBDJbO7qLhQtzO8wtgqIt/VRtnUreNkulb2N3N4Wc/BkEQ==


di9OMkt6WS9xU0JyS2cweDJJbFl3S2UwOTlqY0ljUmYyUUZmbzdpWW1BUU1YMzkrS094NlVmd0t3SkJtRTl2VzgxRGRBVXQydXB0RURQdk02bFFkSHRxUU1kZUdsczduU2RBZExRQStSYkJKZmVNaWdVZmxEdjV2aU9zSkFnNlZNT0wyU242SDdDa1NIdkRrRmNxNjR1RnRtUE9XblJDZ0dvKzArSUJIV0VvPQ==


PwrFGrBEFmCSXzoM5z34ComotQ2xl0iHL+rimtjGqM8inPBMBioMj9jv16G4CJWzGDbA1CUeBXXhQRcs3jyzwhNDzbfKfIWQbIzij9NHdOcreNKqkAtq8KX5HtISYf+DkMTArb3w0dd6X5Zozk3JrA==


Rlk2SHY0UDRLcmlzU251eUR1RnlLd01YTkU1YXJSQ0xVUzlFS2M0YWJsQ3VLYWRwMEp6ZEYwR0RzWkhtMnBteGF3a0VkU1UrWkdBd3VZcTlOTDBhOWVhWlZpSlFla1U2SHBHRUxobVVtRjYwY0Y3emZRRnNvRnU2MFNORzJJd1BRMWxoWExhMEowZFNyOWtTY096dGFnPT0

class Adauth:
    def __init__(self):
        self.secret_key = "SSLQUACKAXOT"
        self.secret_iv = "SLHSAWQOKDGT"
        self.hashed_key = hashlib.sha256(self.secret_key.encode()).hexdigest()[:32]
        self.iv = hashlib.sha256(self.secret_iv.encode()).hexdigest()[:16]


    def ad_auth(self,data):
        payload = self.encrypt_data(pad(data,AES.block_size))
        payload= base64.b64encode(payload.encode()).decode()
        payload='?request='+payload
        url = "http://192.168.103.61:8082/appadmin/index.php/Adservice/login"+payload
        headers = {
                'partner-key': 'AXASN580A23E8WXT',
                'X-IPAddress': '192.168.254.71:5004'
            }
        response = requests.request("GET",url,headers=headers)
        res = json.loads(response.text)
        decrypted_res = self.decrypt_data(res['responseData'])
        print('api decrypted response ',decrypted_res)
        return decrypted_res



    def encrypt_data(self,data):
        cipher = AES.new(self.hashed_key.encode(), AES.MODE_CBC, self.iv.encode())
        encrypted = cipher.encrypt(data)
        return  base64.b64encode(encrypted).decode()

    def decrypt_data(self,data):
        data = base64.b64decode(data)
        cipher = AES.new(self.hashed_key.encode(), AES.MODE_CBC, self.iv.encode())
        return cipher.decrypt(data).decode()

ad = Adauth()

data = b'{ "username":"TP00010885", "password":"Axis@2023", "X-Source":"Portal", "X-SourceChannel":"ABC" }'
print ("Actual string: ", data)
ad.ad_auth(data)



Rlk2SHY0UDRLcmlzU251eUR1RnlLL0ZPNVhYeDJ3dS9vZHROOTBFRGNKK1dVT2dpeHRmYmZQOEpiVUExUTVPWUtaWGZiYWhZbVhDQXM4Ym0vVG9WUXoxNU9rWVd5YkZFVkFHNVIwN1o4enF6dTQvSDVRK2RUeHAyN3M3ckJMd1N2aTVIbnJTYzlybms1MXFTR2t1VW53PT0=

