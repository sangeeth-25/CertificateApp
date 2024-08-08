# CertificateApp


## Open user-routes.js file, copy below code and paste in router.post method

```
const { certificateID, courseName, candidateName, grade, date } = req.body;
        console.log(certificateID);
        if (certDetails.has(certificateID)) {
            res.status(201).json({ message: `${certificateID} already exist` })
        }
        else {
            certDetails.set(certificateID, { courseName, candidateName, grade, date });
            console.log(certDetails.get(certificateID));
            res.status(201).json({ message: 'Certificate details saved' })
        }
```


## Copy below code and paste in router.get method

```
const id1 = req.params.id;
    console.log(id1);
    const details = certDetails.get(id1);
    console.log(details);
    if (details) {
        res.json(details);
    }
    else {
        res.status(404).json({ message: 'details not found' });
    }
```