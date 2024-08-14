### welcom to bmkg-scraper

how to install

```bash
npm install bmkg-scraper

```

how to use it 
```javascript
import { BMKGEarthquake, BMKGWeather, BMKGAreaID } from "bmkg-scraper";

(async function () {
  try { 
    const weather = new BMKGWeather();
    const ponorogo = BMKGAreaID.jawaTimur.kabPonorogo.ponorogo;

    const ponorogoWheather = await weather.jawaTimur(ponorogo);
    console.log(ponorogoWheather);

    const earthquake = new BMKGEarthquake();
    const listEarthquake = await earthquake.list();
    console.log(listEarthquake);
  } catch(e) {
    console.log("error", e);
  }
})();
```

another way how to use :
```javascript
import { BMKGEarthquake, BMKGWeather, BMKGAreaID } from "bmkg-scraper";

async function getWeather(prov, kab, kec) {
  try { 
    let weather = new BMKGWeather();
    let queries = BMKGAreaID[prov][kab][kec];
    let data = await weather[prov](queries);
    console.log(data);

  } catch(e) {
    console.log("error", e);
  }
};

async function getEarthquake() {
 try {
   const earthquake = new BMKGEarthquake();
    const listEarthquake = await earthquake.list();
    console.log(listEarthquake);
  } catch(e) {
    console.log("error", e);
  }
}

let prov = 'jawaTimur';
let kab = 'kabPonorogo';
let kec = 'ponorogo';

getWeather(prov, kab, kec); 
getEarthquake();
```

for more information about BMKGAreaID see [areaid](https://github.com/ka-shifuka/BMKG-scraper/tree/main/src/data/areaIDList)


### info
this package is under development more features in the future
### note
this only work on nodejs 18+
