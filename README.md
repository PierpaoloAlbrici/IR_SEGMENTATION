Esame di Information Retrieval - Pierpaolo Albrici - 960805 - pierpaolo.albrici@studenti.unimi.it

<h3>Struttura</h3>

In <code>Data_PP</code> si trova il codice con il pre processing del dataset. 
La cartella <code>Supervised</code> contiene il codice del modello supervisionato. 
Al suo interno: 
<ul>
  <li><code>Introduction, Background, Footnotes</code>: classificatori della Functional Part Analyzer.</li>
  <li><code>Conclusion</code>: classificatore per la parte di Conclusione Recognizer. </li>
  <li><code>Training</code>: training dei modelli.</li>
  <li><code>Cross Validation</code>: codice per la K - Fold Cross Validation</li>
  <li><code>FeatureExtraction</code>: creazione dei Feature Vector</li>
</ul>

Nella cartella <code>Unsupervised</code> contiene invece il modello non sueprvisionato e il codice per l'utilizzo del modello sueprvisionato sui risultati.
Al suo interno: 
<ul>
  <li><code>Unsupervised</code>: codice per l'algoritmo di segmentazione non supervisionato</li>
  <li><code>IC, SR</code>: codice per il calcolo dell'Information Content e del Word to Vec Model</li>
  <li><code>Evalauation</code>: codice per l'evaluation del modello non supervisionato e dell'applicazione del modello supervisionato per l'etichettatura. </li>
</ul>

<h3>Utilizzo</h3>
<b>Pre Processing</b>
Eseguire il file <code>Data_PP</code>.

<b>Supervised Model</b>
Eseguire il File <code>Training</code> per addestrare i modelli, oppure il file <code>Cross Validation</code> per eseguire la K - Fold Cross Validation e vedere i risutlati. 

<b>Unsupervised Model</b>
Eseguendo il file <code>Evaluation</code> si può eseguire l'evaluation sul modello non supervisionato e su quello supervisionato applicato ai risultati. 
Il risultato è una tupla per ogni configuazione di parametri così composta: <br>
<code>(n, t, Pk, Seg.Error, Uns.Labeling)</code><br>
Dove <code>n</code> e <code>t</code> sono i parametri dell'Unsupervised, <code>Pk</code> e <code>Seg.Error</code> sono gli indici di valutazione 
del modello non supervisionato e <code>Uns.Labeling</code> l'indice di valutazione del modello supervisionato applicat ai risultati. 

Più dettagli sulle metriche di valutazione nel paper. 

<h3>Database</h3>

Nella cartella <code>Dataset / MongoDB </code> sono presenti dei file contenenti le collezioni dei dati in MongoDB. 
<ul>
  <li><code>Dataset</code>: contiene l'intero dataset con le annotazioni</li>
  <li><code>pDataset</code>: contiene il dataset pre processato per il modello supervisionato</li>
  <li><code>relatedness</code>: contiene i valori di relatedness calcolati.</li>
  <li><code>unsDict</code>: dizionario</li>
  <li><code>unsIC</code>: dataset Information Content</li>
</ul>

Il calcolo della relatedness durante la fase di segmentazione non supervisionata in un documento può richiedere diverso tempo. All'interno del della collezione
<code>relatedness</code ci sono dei documenti già analizzati (quelli utilizzati per i test e l'evaluation) che sono: 
<code>[0, 8, 21, 30, 35, 42, 48, 57, 63, 64, 86, 88, 97,99,104,109,113,115,127,128,131,132,133]</code> 
e che quindi possono essere utilizzati per un'analisi veloce del lavoro. 


