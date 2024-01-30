const express = require('express');
const sqlite3 = require('sqlite3');

const app = express();
const port = 3000;


const db = new sqlite3.Database('fantasyFootballDB.db');


app.use(express.json());


app.post('/api/insertData', (req, res) => {
    const { position, nflTeam, heisman, pwr5, ntlChamp, fcs, mvp, winSea, superBowl, rookie, ProBowl, yards, td, extPts } = req.body;

    db.run(
        'INSERT INTO player_data (position, nflTeam, heisman, pwr5, ntlChamp, fcs, mvp, winSea, superBowl, rookie, ProBowl, yards, td, extPts) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)',
        [position, nflTeam, heisman, pwr5, ntlChamp, fcs, mvp, winSea, superBowl, rookie, ProBowl, yards, td, extPts],
        (err) => {
            if (err) {
                console.error(err);
                res.status(500).send('Internal Server Error');
            } else {
                res.status(201).send('Data inserted successfully');
            }
        }
    );
});

app.get('/api/getData', (req, res) => {
    db.all('SELECT * FROM player_data', (err, rows) => {
        if (err) {
            console.error(err);
            res.status(500).send('Internal Server Error');
        } else {
            res.json(rows);
        }
    });
});

app.listen(port, () => {
    console.log(`Server is running on http://localhost:${port}`);
});
