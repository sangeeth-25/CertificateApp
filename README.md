# CertificateApp

## Git Commands

```
git config --global user.name ""//Enter your Github username here
git config --global user.email ""//Enter your Github email ID
```
## SSH Key setting

```
ssh-keygen -t ed25519 -C "recognizable tag" //Replace the recognizable tag with whatever you like
```
```
eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519

cat ~/.ssh/id_ed25519.pub
```
**Copy ssh key (exclude the tag)** 

Now go to the settings and select ssh and gpg keys and paste this key.

Now if you clone using **ssh**. It will automatically be cloned to your local sytem.


## Open user-routes.js file, copy below code and paste in router.post method (inside try)

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


## Copy below code and paste in second router.get method

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

## Open a terminal within the Backend folder, do the following

```
npm install

node index.js

```