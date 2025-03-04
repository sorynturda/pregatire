# Răspunsuri la Top 50 Întrebări pentru Interviu DevOps

## Concepte de bază

### 1. Ce este DevOps și care sunt beneficiile sale?
**Răspuns:** DevOps este o cultură și set de practici care urmărește să unifice dezvoltarea software (Dev) și operațiunile IT (Ops). Scopul principal este de a reduce ciclul de dezvoltare, de a crește frecvența livrărilor și de a asigura implementări mai fiabile.

**Beneficii:**
- Lansări mai rapide și mai frecvente
- Îmbunătățirea colaborării între echipe
- Reducerea ratei de eșec pentru noile lansări
- Rezolvarea mai rapidă a problemelor
- Reducerea complexității
- Îmbunătățirea calității software-ului

### 2. Care sunt principiile de bază ale DevOps?
**Răspuns:** Principiile fundamentale ale DevOps includ:
- Colaborare și comunicare între echipe
- Automatizarea proceselor
- Măsurarea continuă a performanței
- Feedback rapid și îmbunătățire continuă
- Integrare și livrare continuă (CI/CD)
- Responsabilitate partajată
- Focus pe nevoile utilizatorului final

### 3. Explică diferența dintre DevOps și metodologia Agile.
**Răspuns:** Agile se concentrează pe procesul de dezvoltare software, urmărind să livreze software funcțional în iterații scurte prin colaborare cu clientul și adaptare la schimbare. DevOps extinde aceste principii, punând accent pe integrarea echipelor de dezvoltare cu cele de operațiuni, automatizarea proceselor și livrarea continuă. În timp ce Agile se concentrează pe dezvoltarea și livrarea incrementală a software-ului, DevOps se concentrează pe întregul proces, de la dezvoltare până la operațiuni, inclusiv testare, implementare și monitorizare.

### 4. Ce înseamnă "Infrastructure as Code"?
**Răspuns:** Infrastructure as Code (IaC) este practica de a gestiona și proviziona infrastructura IT prin cod în loc de procese manuale. Infrastructura este definită în fișiere de configurare care pot fi versionare, testate și reutilizate, similar cu codul sursă al aplicațiilor. Acest lucru permite gestionarea infrastructurii în mod consistent și repetabil, reducând erorile umane și crescând eficiența. Unelte populare pentru IaC includ Terraform, Ansible, Chef, Puppet și AWS CloudFormation.

### 5. Explică conceptul de "Continuous Integration" și "Continuous Deployment".
**Răspuns:** 
- **Continuous Integration (CI)** este practica prin care dezvoltatorii integrează frecvent codul în repository-ul principal, de obicei de mai multe ori pe zi. Fiecare integrare este verificată automat prin build și teste automate, permițând identificarea și rezolvarea rapidă a erorilor.
- **Continuous Deployment (CD)** este practica de a livra automat fiecare schimbare care trece de toate testele în mediul de producție, fără intervenție umană. Acest lucru permite livrarea rapidă și frecventă a noilor funcționalități către utilizatori.

### 6. Care este diferența dintre Continuous Delivery și Continuous Deployment?
**Răspuns:** Ambele practici implică automatizarea procesului de livrare a software-ului, dar diferă în momentul intervenției umane:
- **Continuous Delivery** automatizează procesul până la un punct în care codul verificat poate fi lansat în producție, dar decizia de lansare efectivă este luată manual.
- **Continuous Deployment** merge un pas mai departe și automatizează întregul proces, inclusiv lansarea în producție, fără intervenție umană. Orice modificare care trece toate testele este lansată automat în producție.

### 7. Ce este un pipeline CI/CD și care sunt componentele sale?
**Răspuns:** Un pipeline CI/CD este un set de procese automate care permit dezvoltatorilor să integreze și să livreze schimbări de cod în mod eficient și sigur. Componentele tipice ale unui pipeline CI/CD includ:
1. **Integrare (CI):** clonarea repository-ului, compilare, rularea testelor unitare
2. **Testare:** testare automată (funcțională, integrare, de performanță)
3. **Securitate:** scanare de vulnerabilități, testare de securitate
4. **Construcție:** crearea artefactelor (cum ar fi imagini Docker)
5. **Deployment în mediu de testare/staging**
6. **Testare în mediu de staging**
7. **Aprobarea lansării** (în cazul Continuous Delivery)
8. **Deployment în producție**
9. **Monitorizare și feedback**

### 8. Explică conceptul de "shift left" în DevOps.
**Răspuns:** "Shift left" în DevOps se referă la mutarea testării, securității și altor activități critice mai devreme în ciclul de dezvoltare (spre "stânga" în reprezentarea liniară a procesului de dezvoltare). Aceasta înseamnă că testarea și securitatea sunt integrate de la începutul ciclului de dezvoltare, nu doar la final. Beneficiile includ identificarea timpurie a problemelor când sunt mai ieftine și mai ușor de rezolvat, reducerea costurilor și îmbunătățirea calității produsului final.

### 9. Ce este "Configuration Management" și de ce este important?
**Răspuns:** Configuration Management este procesul de menținere a sistemelor IT, a serverelor și a software-ului în starea dorită și consistentă. Acesta implică definirea configurațiilor sistemelor, controlul versiunilor configurațiilor, și asigurarea că toate sistemele sunt configurate corect și consecvent.

Este important deoarece:
- Reduce riscul de erori cauzate de configurări inconsistente
- Facilitează scalarea prin aplicarea configurațiilor identice pe multiple sisteme
- Îmbunătățește auditabilitatea prin înregistrarea schimbărilor de configurație
- Permite recuperarea rapidă după incidente
- Susține Infrastructure as Code pentru automatizarea infrastructurii

Unelte populare includ Ansible, Chef, Puppet și SaltStack.

### 10. Ce înțelegi prin "Microservices Architecture"?
**Răspuns:** Arhitectura de microservicii este o abordare de dezvoltare software în care o aplicație este construită ca un set de servicii mici, independente, care rulează în propriile procese și comunică prin mecanisme ușoare, adesea API-uri HTTP.

Caracteristici principale:
- Servicii independente, fiecare cu o singură responsabilitate
- Fiecare microserviciu poate fi dezvoltat, testat, implementat și scalat independent
- Serviciile pot fi scrise în diferite limbaje de programare și pot utiliza diferite tehnologii de stocare a datelor
- Comunicare între servicii prin API-uri bine definite
- Organizare în jurul capabilităților de business

Avantajele includ dezvoltare mai rapidă, scalabilitate îmbunătățită, reziliență mai bună și posibilitatea de a adopta noi tehnologii mai ușor. Dezavantajele includ complexitatea crescută a sistemului distribuit și provocări în testare și debugging.

## Control versiune și Git

### 11. Ce este Git și care sunt avantajele sale?
**Răspuns:** Git este un sistem de control al versiunilor distribuit, creat pentru a gestiona proiecte de orice dimensiune cu viteză și eficiență. Acesta urmărește modificările în fișiere, permitând colaborarea între dezvoltatori.

Avantaje:
- Sistem distribuit - fiecare dezvoltator are o copie completă a repository-ului
- Branching și merging eficiente și rapide
- Performanță bună chiar și pentru proiecte mari
- Integritate a datelor prin hashuri SHA-1
- Posibilitatea de a lucra offline
- Flexibilitate în fluxurile de lucru
- Suport excelent pentru dezvoltarea non-liniară (branching)
- Ecosistem vast de unelte și platforme (GitHub, GitLab, Bitbucket)

### 12. Explică diferența dintre Git și SVN.
**Răspuns:** Principalele diferențe între Git și SVN (Subversion) sunt:

- **Arhitectură:** Git este un sistem distribuit, în timp ce SVN este centralizat. În Git, fiecare dezvoltator are o copie completă a repository-ului, inclusiv istoricul, în timp ce în SVN, există un singur repository central.
- **Branching:** În Git, branch-urile sunt ușor de creat și de unit (merge), fiind o operație locală rapidă. În SVN, branch-urile sunt mai grele și implică copierea fișierelor pe server.
- **Conectivitate:** Git permite lucrul offline cu commit-uri locale, în timp ce SVN necesită conexiune la server pentru majoritatea operațiunilor.
- **Dimensiune:** Repository-urile Git pot fi mai mari din cauza stocării copiei complete a istoricului local.
- **Performanță:** Git este în general mai rapid pentru majoritatea operațiunilor.
- **Curba de învățare:** SVN tinde să aibă o curbă de învățare mai ușoară, în timp ce Git poate fi mai complex la început.

### 13. Care sunt comenzile Git pe care le folosești frecvent?
**Răspuns:** Comenzile Git frecvent utilizate includ:
- `git init` - inițializarea unui repository
- `git clone` - clonarea unui repository existent
- `git add` - adăugarea fișierelor în staging area
- `git commit` - salvarea modificărilor în repository
- `git status` - verificarea stării repository-ului
- `git pull` - preluarea și integrarea modificărilor de la remote
- `git push` - trimiterea modificărilor locale la repository-ul remote
- `git branch` - listarea, crearea sau ștergerea branch-urilor
- `git checkout` / `git switch` - comutarea între branch-uri
- `git merge` - unirea modificărilor din branch-uri diferite
- `git log` - vizualizarea istoricului commit-urilor
- `git fetch` - descărcarea modificărilor de la remote fără a le integra
- `git diff` - afișarea diferențelor între versiuni
- `git stash` - salvarea temporară a modificărilor necommit-ate

### 14. Ce este un Git branch și cum îl folosești?
**Răspuns:** Un branch în Git este o linie independentă de dezvoltare. Branch-urile permit dezvoltatorilor să lucreze în paralel pe funcționalități sau corecții diferite fără a afecta branch-ul principal (de obicei numit "main" sau "master").

Cum folosești branch-urile:
1. **Crearea unui branch:** `git branch nume-branch` sau `git checkout -b nume-branch` (creează și comută pe noul branch)
2. **Comutarea între branch-uri:** `git checkout nume-branch` sau `git switch nume-branch`
3. **Listarea branch-urilor:** `git branch`
4. **Push branch la remote:** `git push -u origin nume-branch`
5. **Unirea (merge) unui branch:** Mai întâi comutați pe branch-ul destinație (ex. main), apoi `git merge nume-branch`
6. **Ștergerea unui branch:** `git branch -d nume-branch` (local) și `git push origin --delete nume-branch` (remote)

Branch-urile sunt folosite în diverse strategii de dezvoltare, cum ar fi feature branching (un branch pentru fiecare funcționalitate) sau gitflow (branch-uri dedicate pentru dezvoltare, funcționalități, release-uri și hotfix-uri).

### 15. Explică procesul de Git rebase vs. Git merge.
**Răspuns:** Ambele comenzi sunt folosite pentru a integra modificări dintr-un branch în altul, dar funcționează diferit:

**Git merge:**
- Creează un nou commit de merge care unește istoricul celor două branch-uri
- Păstrează istoricul exact al branch-urilor (când și unde au divergat și s-au unit)
- Este non-distructiv, nu modifică commit-urile existente
- Rezultatul este un istoric de tip "branch și merge" vizibil în graficul repository-ului

**Git rebase:**
- Mută sau "replantează" un întreg branch pe vârful altui branch
- Rescrie istoricul prin crearea de noi commit-uri pentru fiecare commit din branch-ul original
- Rezultă într-un istoric liniar, ca și cum toate modificările ar fi fost făcute secvențial
- Util pentru a menține un istoric curat, dar poate complica colaborarea dacă este folosit pe branch-uri publice

**Când să folosești fiecare:**
- **Merge** - pentru branch-uri de feature care sunt partajate public
- **Rebase** - pentru a curăța branch-uri locale înainte de a le integra în branch-ul principal sau pentru a aduce un branch la zi cu ultimele modificări din branch-ul principal

### 16. Ce este Git cherry-pick și când l-ai folosi?
**Răspuns:** Git cherry-pick este o comandă care permite aplicarea selectivă a unui commit specific din un branch în alt branch, fără a integra toate modificările intermediare. Sintaxa de bază este `git cherry-pick <commit-hash>`.

Scenarii în care cherry-pick este util:
1. **Hotfix-uri** - când trebuie să aplici o corecție urgentă din development în branch-ul de producție
2. **Recuperarea modificărilor** - când dorești să recuperezi modificări specifice dintr-un branch abandonat
3. **Reorganizarea commit-urilor** - când dorești să aplici anumite modificări într-o ordine diferită
4. **Backporting** - aplicarea unei corecții din versiunea nouă în versiuni mai vechi care sunt încă menținute
5. **Selecție pentru release** - alegerea anumitor funcționalități pentru un release fără a include altele care nu sunt gata

Este important de menționat că cherry-pick creează un nou commit cu un hash diferit, ceea ce poate complica istoricul dacă este folosit frecvent.

### 17. Cum rezolvi conflictele în Git?
**Răspuns:** Rezolvarea conflictelor în Git implică următorii pași:

1. **Identificarea conflictelor** - După un merge sau rebase, Git marchează fișierele cu conflicte
2. **Deschiderea fișierelor cu conflicte** - Git marchează zonele conflictuale cu delimitatori speciali:
   ```
   <<<<<<< HEAD
   Conținutul din branch-ul curent
   =======
   Conținutul din branch-ul de integrat
   >>>>>>> branch-name
   ```
3. **Editarea fișierelor** - Modificați manual fișierele pentru a rezolva conflictele, alegând ce conținut să păstrați
4. **Eliminarea marcajelor** - Ștergeți delimitatorii <<<<<<, ======= și >>>>>>>
5. **Marcarea ca rezolvate** - Folosiți `git add <file>` pentru a marca fișierele ca rezolvate
6. **Finalizarea operațiunii** - Continuați cu `git merge --continue` sau `git rebase --continue`

Unelte care pot ajuta:
- Editoare de text și IDE-uri cu suport pentru rezolvarea conflictelor (VS Code, IntelliJ)
- Unelte vizuale precum `git mergetool`
- Pentru situații complexe, folosiți `git log` și `git show` pentru a înțelege contextul modificărilor

### 18. Explică conceptul de Git workflow și dă un exemplu.
**Răspuns:** Un Git workflow este o recomandare pentru modul în care să folosiți Git pentru a realiza lucrul în mod consistent și productiv. Acesta definește cum sunt create branch-urile, cum sunt integrate modificările și cum se face colaborarea între dezvoltatori.

**Exemplu: Gitflow Workflow**
Gitflow este unul dintre cele mai populare workflow-uri și implică utilizarea următoarelor tipuri de branch-uri:

1. **master/main** - conține codul de producție, stabil. Doar cod testat și verificat ajunge aici.
2. **develop** - branch principal de dezvoltare, conține ultimele modificări pentru următorul release.
3. **feature/** - branch-uri pentru dezvoltarea noilor funcționalități, create din develop.
4. **release/** - branch-uri pentru pregătirea unui nou release, permit finalizarea și testarea.
5. **hotfix/** - branch-uri pentru corecții urgente în producție, create din master.

Fluxul tipic este:
- Dezvoltatorii creează branch-uri feature din develop
- Când feature-ul e gata, este unit (merge) înapoi în develop
- Când develop e gata pentru release, se creează un branch release
- După testare și pregătire, release se unește atât în master cât și în develop
- Dacă apar probleme în producție, se creează un hotfix din master, apoi se unește înapoi în master și develop

Alte workflow-uri populare includ GitHub Flow (mai simplu, orientat pe feature branches și pull requests) și Trunk-Based Development (focusat pe integrarea frecventă în branch-ul principal).

## Containere și Orchestrare

### 19. Ce este Docker și care sunt avantajele sale?
**Răspuns:** Docker este o platformă deschisă pentru dezvoltarea, livrarea și rularea aplicațiilor în containere. Containerele sunt unități standardizate de software care includ tot ce are nevoie o aplicație pentru a rula: cod, runtime, biblioteci și dependințe.

**Avantaje:**
- **Portabilitate** - containerele rulează consistent pe orice platformă care suportă Docker
- **Izolare** - aplicațiile și dependențele lor sunt izolate, evitând conflictele
- **Eficiență** - containerele partajează kernel-ul OS și utilizează mai puține resurse decât mașinile virtuale
- **Viteză** - containerele pornesc în secunde, comparativ cu minutele necesare mașinilor virtuale
- **DevOps și CI/CD** - facilitează implementarea continuă și integrarea continuă
- **Scalabilitate** - ușor de scalat orizontal și de orchestrat cu unelte precum Kubernetes
- **Control al versiunilor** - imagini imutabile cu versiuni clare
- **Densitate** - posibilitatea de a rula mai multe containere pe aceeași infrastructură

### 20. Explică diferența dintre o mașină virtuală și un container.
**Răspuns:** Principalele diferențe între containere și mașini virtuale (VM) sunt:

**Mașini Virtuale:**
- Virtualizează hardware-ul complet, oferind un sistem de operare complet
- Fiecare VM include propriul kernel de OS
- Necesită un hypervisor (VMware, VirtualBox, Hyper-V) pentru a funcționa
- Consuma mai multe resurse (GB de memorie, mai mult spațiu de stocare)
- Pornire și oprire mai lentă (minute)
- Izolare completă la nivel de sistem de operare

**Containere:**
- Virtualizează doar la nivelul sistemului de operare
- Partajează kernel-ul sistemului de operare gazdă
- Rulează direct pe sistemul de operare gazdă, fără hypervisor
- Consumă mult mai puține resurse (MB de memorie, mai puțin spațiu)
- Pornire și oprire foarte rapidă (secunde)
- Izolare la nivel de proces, dar nu la fel de completă ca VM-urile

Arhitectural, o VM include un stack hardware-hypervisor-OS-aplicații, în timp ce un container include doar aplicația și dependențele ei, rulând pe kernel-ul gazdei.

### 21. Care sunt componentele principale ale Docker?
**Răspuns:** Componentele principale ale ecosistemului Docker sunt:

1. **Docker Engine** - motorul core care permite crearea și rularea containerelor
   - **dockerd** - daemon-ul care gestionează obiecte Docker (imagini, containere, volume, rețele)
   - **Docker CLI** - interfața în linia de comandă pentru interacțiunea cu Docker

2. **Docker Images** - template-uri read-only care conțin instrucțiunile pentru crearea containerelor
   - Stocate în layere pentru eficiență și reutilizare

3. **Docker Containers** - instanțe rulabile ale imaginilor Docker

4. **Docker Registry** - depozit pentru stocarea și distribuirea imaginilor Docker
   - **Docker Hub** - registry public oficial
   - Registries private pentru uz corporativ

5. **Docker Compose** - unealtă pentru definirea și rularea aplicațiilor multi-container

6. **Docker Swarm** - unealtă de orchestrare nativă pentru clustere Docker (alternativă la Kubernetes)

7. **Docker Volumes** - mecanism persistent de stocare a datelor pentru containere

8. **Docker Networks** - rețele virtuale pentru comunicarea între containere

### 22. Ce este un Dockerfile și ce conține?
**Răspuns:** Un Dockerfile este un fișier text care conține o serie de instrucțiuni pentru construirea automată a unei imagini Docker. Acesta definește mediul de rulare al containerului, inclusiv sistemul de operare, software-ul necesar, variabilele de mediu și comenzile care trebuie executate.

Elementele comune ale unui Dockerfile includ:

1. **FROM** - imaginea de bază de la care se pornește (ex: `FROM ubuntu:22.04`)
2. **RUN** - comenzi pentru instalarea pachetelor și dependențelor
3. **COPY/ADD** - copierea fișierelor din sistemul local în imagine
4. **WORKDIR** - setarea directorului de lucru pentru instrucțiunile ulterioare
5. **ENV** - definirea variabilelor de mediu
6. **EXPOSE** - specificarea porturilor pe care containerul le va asculta
7. **CMD/ENTRYPOINT** - comanda implicită care va fi executată la pornirea containerului
8. **VOLUME** - crearea unui punct de montare pentru date persistente
9. **USER** - setarea utilizatorului care va rula procesele din container
10. **ARG** - definirea argumentelor pentru construirea imaginii

Exemplu simplificat pentru o aplicație Node.js:
```dockerfile
FROM node:16-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### 23. Ce este Docker Compose și când îl folosești?
**Răspuns:** Docker Compose este o unealtă pentru definirea și rularea aplicațiilor Docker multi-container. Permite definirea întregii stive de aplicații (inclusiv servicii, rețele și volume) într-un singur fișier YAML, simplificând gestionarea mediilor complexe.

**Când folosești Docker Compose:**
1. **Medii de dezvoltare** - simplifică configurarea mediilor locale consistente pentru toți dezvoltatorii
2. **Testare automatizată** - crearea rapidă a mediilor izolate pentru teste
3. **Aplicații cu mai multe servicii** - când aplicația constă din mai multe containere care trebuie să funcționeze împreună
4. **Demonstrații și POC-uri** - pentru a împărtăși ușor configurația aplicației
5. **CI/CD** - parte a pipeline-urilor de integrare/livrare continuă

**Exemplu simplificat de docker-compose.yml:**
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "8000:8000"
    depends_on:
      - db
  db:
    image: postgres:14
    volumes:
      - postgres_data:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=example
volumes:
  postgres_data:
```

Cu acest fișier, întreaga aplicație poate fi pornită cu o singură comandă: `docker-compose up`.

### 24. Ce este Kubernetes și ce probleme rezolvă?
**Răspuns:** Kubernetes (K8s) este o platformă open-source pentru orchestrarea containerelor, proiectată pentru automatizarea implementării, scalării și gestionării aplicațiilor containerizate.

**Probleme pe care le rezolvă:**
1. **Scalarea automată** - ajustează numărul de containere în funcție de cerere
2. **Self-healing** - repornește automat containerele care eșuează, înlocuiește și reprogramează containerele când nodurile mor
3. **Deployment automatizat** - permite actualizarea graduală a aplicațiilor fără downtime (rolling updates)
4. **Load balancing** - distribuie traficul de rețea pentru a asigura stabilitatea implementării
5. **Storage orchestration** - integrează automat sisteme de stocare
6. **Secret management** - gestionează informații sensibile cum ar fi parole și chei
7. **Multi-cloud și hibrid** - poate rula atât în cloud cât și on-premises
8. **Configurare declarativă** - permite definirea stării dorite a aplicațiilor, iar Kubernetes se ocupă de menținerea acestei stări

Kubernetes devine esențial când trebuie să gestionezi aplicații complexe, distribuite în containere, care necesită scalabilitate și disponibilitate ridicată.

### 25. Explică conceptul de pod, deployment și service în Kubernetes.
**Răspuns:** 

**Pod:**
- Cea mai mică unitate de deployment în Kubernetes
- Conține unul sau mai multe containere care partajează resurse (spațiu de rețea, volume)
- Containerele dintr-un pod rulează întotdeauna pe același nod și sunt programate împreună
- Pot comunica între ele folosind localhost
- Sunt efemere - pot fi create, distruse și înlocuite dinamic

**Deployment:**
- Controller care asigură gestionarea Pods și ReplicaSets
- Permite actualizări declarative pentru Pods și ReplicaSets
- Definește starea dorită a aplicației (ce imagini să ruleze, câte replici, etc.)
- Gestionează actualizările aplicației cu strategii precum rolling update
- Permite rollback la versiuni anterioare
- Oferă posibilitatea de a scala numărul de Pod-uri

**Service:**
- Abstractizare care definește un set logic de Pods și o politică de acces la acestea
- Oferă o adresă IP și DNS stabile, independente de Pod-urile individuale
- Permite load balancing între Pod-uri
- Descoperă Pod-urile prin selectors
- Tipuri principale de Service:
  - **ClusterIP** - expune Service-ul doar în interiorul clusterului
  - **NodePort** - expune Service-ul pe un port specific pe fiecare nod
  - **LoadBalancer** - expune Service-ul extern folosind un load balancer cloud
  - **ExternalName** - mapează Service-ul la un nume DNS extern

### 26. Cum se face scalarea în Kubernetes?
**Răspuns:** Kubernetes oferă mai multe mecanisme de scalare:

**1. Scalare manuală:**
- Folosind comanda `kubectl scale deployment <nume> --replicas=<număr>`
- Modificând direct numărul de replici în fișierul de configurare YAML

**2. Scalare orizontală automată (Horizontal Pod Autoscaler - HPA):**
- Ajustează automat numărul de Pod-uri într-un Deployment, ReplicaSet sau StatefulSet
- Bazat pe utilizarea CPU, memorie sau metrici personalizate
- Configurare prin resursa `HorizontalPodAutoscaler`:
  ```yaml
  apiVersion: autoscaling/v2
  kind: HorizontalPodAutoscaler
  metadata:
    name: example-hpa
  spec:
    scaleTargetRef:
      apiVersion: apps/v1
      kind: Deployment
      name: example-deployment
    minReplicas: 2
    maxReplicas: 10
    metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 50
  ```

**3. Scalare verticală automată (Vertical Pod Autoscaler - VPA):**
- Ajustează automat cerințele de CPU și memorie ale containerelor
- Util pentru aplicații care nu pot fi ușor scalate orizontal

**4. Cluster Autoscaler:**
- Ajustează numărul de noduri din cluster în funcție de necesar
- Adaugă noduri când Pod-urile nu pot fi programate din cauza resurselor insuficiente
- Elimină noduri când acestea nu sunt necesare

**5. Scalare bazată pe evenimente (Kubernetes Event-driven Autoscaling - KEDA):**
- Permite scalarea bazată pe evenimente din surse externe (cozi de mesaje, senzori, etc.)

### 27. Ce este un Helm chart?
**Răspuns:** Helm este un manager de pachete pentru Kubernetes, iar un Helm chart este un pachet care conține toate resursele Kubernetes necesare pentru a implementa o aplicație în cluster.

**Componente ale unui Helm chart:**
1. **Chart.yaml** - Metadata despre chart (nume, versiune, descriere)
2. **values.yaml** - Valorile implicite de configurare care pot fi suprascrise
3. **templates/** - Director cu template-uri de manifeste Kubernetes
4. **charts/** - Director opțional pentru charts dependente
5. **README.md** - Documentație pentru utilizatori
6. **LICENSE** - Licența pentru chart
7. **requirements.yaml** - Dependențe pentru chart (în Helm v2) sau în Chart.yaml (Helm v3)

**Beneficii ale utilizării Helm:**
- **Gestionarea complexității** - simplifică implementarea aplicațiilor complexe cu multe componente
- **Reutilizarea** - aceleași charts pot fi utilizate în medii diferite
- **Versionare** - charts pot fi versionate, facilitând implementarea unor versiuni specifice
- **Management al configurațiilor** - permite personalizarea implementărilor prin valori configurabile
- **Rollbacks** - simplificarea revenirii la versiuni anterioare
- **Comunitate** - acces la un repository public de charts predefinite (Artifact Hub)

Exemplu de utilizare:
```bash
# Instalarea unei aplicații folosind Helm
helm install my-release bitnami/wordpress

# Personalizarea instalării cu valori specifice
helm install my-release bitnami/wordpress --values=custom-values.yaml
```

## Automatizare și Infrastructură

### 28. Ce instrumente de automatizare cunoști (Ansible, Terraform, etc.)?
**Răspuns:** Principalele instrumente de automatizare pentru DevOps includ:

1. **Terraform** - pentru Infrastructure as Code, gestionează infrastructura în multiple cloud-uri și servicii
2. **Ansible** - pentru configurarea sistemelor și implementarea aplicațiilor, folosește YAML și nu necesită agent
3. **Puppet** - pentru gestionarea configurațiilor, folosește un limbaj propriu declarativ
4. **Chef** - pentru automatizarea infrastructurii, folosește DSL bazat pe Ruby
5. **SaltStack** - pentru automatizarea infrastructurii și gestionarea configurațiilor
6. **Jenkins** - pentru integrare și livrare continuă
7. **GitLab CI/CD** - pentru automatizarea CI/CD integrată cu GitLab
8. **GitHub Actions** - pentru automatizarea workflow-urilor integrată cu GitHub
9. **CircleCI** - platformă cloud pentru CI/CD
10. **Pulumi** - IaC folosind limbaje de programare familiare (Python, TypeScript)

Fiecare instrument are puncte forte pentru anumite scenarii și multe organizații folosesc o combinație de acestea.

### 29. Ce este Terraform și cum funcționează?
**Răspuns:** Terraform este o unealtă open-source de Infrastructure as Code (IaC) dezvoltată de HashiCorp. Permite definirea și provizionarea infrastructurii într-un mod declarativ, folosind un limbaj de configurare numit HashiCorp Configuration Language (HCL).

**Cum funcționează:**
1. **Scrii cod** - Definești infrastructura dorită în fișiere .tf folosind HCL
2. **Plan** - Terraform analizează codul și generează un plan de execuție care arată ce resurse vor fi create/modificate/șterse
3. **Apply** - Terraform creează/modifică/șterge resursele conform planului
4. **State** - Terraform menține un fișier de stare care ține evidența resurselor gestionate

**Concepte cheie:**
- **Providers** - Plugin-uri care permit Terraform să interacționeze cu diverse platforme (AWS, Azure, GCP, etc.)
- **Resources** - Componentele infrastructurii pe care le gestionezi (VMs, rețele, DNS, etc.)
- **Modules** - Colecții reutilizabile de resurse
- **State** - Starea curentă a infrastructurii
- **Variables & Outputs** - Pentru parametrizare și returnarea valorilor
- **Backends** - Unde și cum este stocat fișierul de stare

**Exemplu simplu pentru AWS:**
```hcl
provider "aws" {
  region = "eu-west-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  
  tags = {
    Name = "example-instance"
  }
}
```

### 30. Care este diferența dintre Ansible și Terraform?
**Răspuns:** Deși ambele sunt instrumente de automatizare a infrastructurii, ele au scopuri și abordări diferite:

**Terraform:**
- **Scop principal:** Infrastructure as Code (IaC) - provizionarea resurselor
- **Paradigmă:** Declarativă - specifici starea finală dorită
- **State management:** Menține un fișier de stare pentru a urmări resursele
- **Idempotență:** Asigurată prin fișierul de stare
- **Limbaj:** HashiCorp Configuration Language (HCL)
- **Specializare:** Excelent pentru crearea și gestionarea infrastructurii cloud
- **Arhitectură:** Fără agenți

**Ansible:**
- **Scop principal:** Configuration Management - configurarea sistemelor existente
- **Paradigmă:** Procedurală (deși folosește YAML declarativ)
- **State management:** Fără state explicit, verifică sistemul țintă în timp real
- **Idempotență:** Integrată în module, dar depinde de implementare
- **Limbaj:** YAML (Playbooks)
- **Specializare:** Excelent pentru configurarea sistemelor după ce au fost create
- **Arhitectură:** Fără agenți, folosește SSH pentru comunicare

**Utilizare complementară:**
Multe organizații folosesc ambele instrumente împreună:
- Terraform pentru provizionarea infrastructurii (VM-uri, rețele, etc.)
- Ansible pentru configurarea sistemelor create (instalare software, configurare servicii)

### 31. Explică conceptul de "idempotență" în automatizare.
**Răspuns:** Idempotența este o proprietate a unei operații prin care aplicarea repetată a aceleiași operații nu produce un rezultat diferit după prima aplicare. În contextul DevOps și automatizării, acest concept este esențial.

**În practică, idempotența înseamnă că:**
- Același script sau comandă poate fi executat de mai multe ori fără a provoca efecte secundare nedorite
- Dacă sistemul este deja în starea dorită, nicio schimbare nu va fi făcută
- Dacă operația eșuează la mijloc, poate fi reluată în siguranță

**Beneficii:**
- **Siguranță** în execuție repetată
- **Predictibilitate** - rezultatul final este cunoscut
- **Rezistență la erori** - operațiile pot fi reluate după eșecuri
- **Reducerea complexității** în gestionarea stării

**Exemple de operații idempotente:**
- Crearea unui utilizator dacă nu există (nu va crea duplicate)
- Setarea permisiunilor unui fișier la o valoare specifică (aplicarea repetată produce același rezultat)
- HTTP GET (citirea repetată nu modifică resursele)

**Exemple de operații non-idempotente:**
- Adăugarea unei înregistrări într-o bază de date fără verificări (va crea duplicate)
- Incrementarea unui contor
- HTTP POST (creează de obicei noi resurse la fiecare apel)

Unelte precum Ansible, Terraform și Chef sunt proiectate să fie idempotente, ceea ce le face potrivite pentru automatizarea infrastructurii.

### 32. Ce este cloud computing și care sunt principalele modele de servicii (IaaS, PaaS, SaaS)?
**Răspuns:** Cloud computing este un model de livrare a serviciilor IT care oferă acces la resurse computaționale (servere, stocare, baze de date, rețele, software) prin internet, fără a necesita gestionarea directă a infrastructurii fizice.

**Principalele modele de servicii:**

**1. Infrastructure as a Service (IaaS):**
- Furnizează resurse computaționale virtualizate
- Utilizatorul gestionează OS, middleware, aplicații
- Furnizorul gestionează hardware-ul, virtualizarea, rețeaua, stocarea
- Exemple: AWS EC2, Azure Virtual Machines, Google Compute Engine

**2. Platform as a Service (PaaS):**
- Furnizează o platformă completă pentru dezvoltarea, rularea și gestionarea aplicațiilor
- Utilizatorul gestionează doar aplicațiile și datele
- Furnizorul gestionează hardware-ul, OS-ul, middleware-ul
- Elimină necesitatea de a gestiona infrastructura subjacenta
- Exemple: AWS Elastic Beanstalk, Azure App Service, Google App Engine, Heroku

**3. Software as a Service (SaaS):**
- Furnizează aplicații complete, gata de utilizat prin internet
- Utilizatorul doar folosește aplicația
- Furnizorul gestionează tot, de la hardware până la aplicație
- De obicei accesat prin browser web sau API
- Exemple: Google Workspace, Microsoft 365, Salesforce, Slack

**Alte modele importante:**
- **Function as a Service (FaaS)** / **Serverless**: AWS Lambda, Azure Functions
- **Container as a Service (CaaS)**: AWS ECS/EKS, Azure AKS, Google GKE
- **Database as a Service (DBaaS)**: AWS RDS, Azure SQL Database
- **Storage as a Service**: AWS S3, Azure Blob Storage

### 33. Explică diferența dintre AWS, Azure și Google Cloud.
**Răspuns:** AWS, Azure și Google Cloud sunt cei trei furnizori principali de cloud public, fiecare cu propriile puncte forte, servicii și caracteristici:

**AWS (Amazon Web Services):**
- **Piață:** Lider de piață, cea mai mare cotă de piață
- **Maturitate:** Primul mare furnizor cloud (lansat în 2006), cel mai matur
- **Puncte forte:** Cel mai vast ecosistem de servicii, servicii avansate pentru enterprise, prezență globală extinsă
- **Servicii notabile:** EC2, S3, DynamoDB, Lambda, VPC
- **Abordare:** Oferă multiple soluții pentru aceeași problemă, foarte flexibil
- **Regiuni/Zone:** Cea mai mare acoperire globală

**Microsoft Azure:**
- **Piață:** Al doilea ca mărime, popular în mediile enterprise
- **Maturitate:** Lansat în 2010, creștere rapidă
- **Puncte forte:** Integrare excelentă cu ecosistemul Microsoft (Windows, Active Directory, Office 365), soluții hibride
- **Servicii notabile:** Azure VMs, Azure SQL, Azure Functions, Azure Active Directory
- **Abordare:** Orientat spre enterprise, integrare puternică cu soluții on-premises
- **Avantaj distinctiv:** Azure DevOps și integrarea cu .NET

**Google Cloud Platform (GCP):**
- **Piață:** Al treilea ca mărime, dar în creștere
- **Maturitate:** Cel mai nou dintre cei trei mari (lansat complet în 2011)
- **Puncte forte:** Infrastructură de rețea superioară, Big Data și ML/AI, container-native
- **Servicii notabile:** Compute Engine, BigQuery, Kubernetes Engine, TensorFlow
- **Abordare:** Design simplu și elegant, orientat spre dezvoltatori
- **Avantaj distinctiv:** Leadership în Kubernetes și tehnologii open-source

**Diferențe în abordare:**
- **Prețuri:** Modele diferite de cost, GCP având adesea prețuri competitive
- **Interfețe:** AWS poate părea complex pentru începători, GCP tinde să fie mai simplu
- **Enterprise vs. Startup:** Azure foarte orientat spre enterprise, GCP popular în startups

**Considerații pentru alegere:**
- Tehnologiile existente și integrări
- Competențele echipei
- Cerințele specifice ale aplicației
- Constrângerile bugetare
- Cerințele de conformitate

### 34. Cum implementezi o infrastructură multi-cloud?
**Răspuns:** Implementarea unei infrastructuri multi-cloud implică utilizarea serviciilor de la mai mulți furnizori cloud pentru a evita dependența de un singur furnizor și a beneficia de avantajele fiecăruia.

**Strategii de implementare:**

1. **Abstractizare și portabilitate:**
   - Folosirea unor unelte precum Terraform pentru a abstractiza infrastructura
   - Containerizarea aplicațiilor cu Docker
   - Orchestrarea cu Kubernetes pentru portabilitate între cloud-uri
   - Utilizarea de API-uri și servicii standardizate când este posibil

2. **Segmentare pe funcționalități:**
   - Rularea diferitelor componente ale aplicației în cloud-uri diferite
   - Exemplu: compute în AWS, storage în GCP, ML în Azure

3. **Redundanță și DR:**
   - Utilizarea unui cloud primar pentru operațiuni normale
   - Al doilea cloud pentru backup și disaster recovery

**Instrumente și tehnici:**
- **Terraform** - pentru IaC independent de furnizor
- **Kubernetes** - pentru orchestrarea containerelor între cloud-uri
- **Service mesh** (Istio, Linkerd) - pentru networking și observabilitate
- **CI/CD tools** - pentru deployment consistent pe multiple cloud-uri
- **API Gateways** - pentru a abstractiza backend-urile
- **Monitoring unificat** - pentru a avea o viziune de ansamblu

**Provocări:**
- **Complexitate crescută** - în administrare și management
- **Latență între cloud-uri** - poate afecta performanța
- **Costuri potențial mai mari** - fără discount-uri pentru volum mare
- **Securitate** - politici consistente între furnizori
- **Networking** - conectarea eficientă a cloud-urilor
- **Competențe** - necesită cunoașterea mai multor platforme

**Best practices:**
- Proiectarea pentru eșec și reziliență
- Automatizarea completă a implementării
- Menținerea unei documentații riguroase
- Implementarea unui monitoring centralizat
- Utilizarea unor politici de securitate uniforme
- Evaluarea cost-beneficiu pentru fiecare workload

## Monitorizare și Logging

### 35. Ce instrumente de monitorizare cunoști?
**Răspuns:** Iată o listă a celor mai populare instrumente de monitorizare folosite în ecosistemul DevOps:

**Monitoring de sistem și infrastructură:**
- **Prometheus** - sistem de monitorizare open-source, ideal pentru medii Kubernetes
- **Grafana** - platformă de vizualizare a datelor, adesea folosită cu Prometheus
- **Nagios** - monitoring clasic, de tip check-based
- **Zabbix** - platformă completă de monitoring enterprise
- **Datadog** - platformă SaaS de monitoring și analytics
- **New Relic** - platformă de observabilitate pentru aplicații și infrastructură
- **Dynatrace** - monitorizare AI-powered pentru aplicații și infrastructură
- **CloudWatch** (AWS) - monitoring pentru serviciile și resursele AWS
- **Azure Monitor** - monitoring pentru serviciile și resursele Azure
- **Stackdriver** (Google Cloud) - monitoring pentru serviciile GCP

**Logging și analiza logurilor:**
- **ELK Stack** (Elasticsearch, Logstash, Kibana) - collectare, prelucrare și vizualizare loguri
- **Fluentd** - colector de date unificat
- **Graylog** - management centralizat al logurilor
- **Splunk** - platformă enterprise pentru analiza datelor de logging
- **Loki** - sistem de agregare de loguri inspirat din Prometheus

**Tracing distribuit:**
- **Jaeger** - pentru monitorizarea și troubleshooting-ul sistemelor distribuite
- **Zipkin** - sistem de tracing distribuit
- **OpenTelemetry** - framework și standarde pentru instrumentare

**Monitorizare de aplicații (APM):**
- **AppDynamics** - monitorizarea performanței aplicațiilor
- **Elastic APM** - parte din ecosistemul Elastic
- **Instana** - observabilitate automată pentru aplicații moderne

**Monitoring pentru end-user experience:**
- **Pingdom** - monitorizarea disponibilității serviciilor
- **Uptime Robot** - verificări simple de disponibilitate
- **Lighthouse** - tool pentru analiza performanței site-urilor web

### 36. Ce este Prometheus și cum funcționează?
**Răspuns:** Prometheus este un sistem de monitorizare și alertare open-source, inițial dezvoltat la SoundCloud. Este acum un proiect independent și unul dintre proiectele de bază ale Cloud Native Computing Foundation (CNCF).

**Cum funcționează Prometheus:**

1. **Model de date time-series:**
   - Stochează toate datele ca serii temporale
   - Fiecare serie temporală este identificată prin numele metricii și perechi cheie-valoare (labels)

2. **Arhitectură pull-based:**
   - Prometheus adună (scrape) metrici de la ținte prin HTTP
   - Țintele expun metrici la un endpoint HTTP (de obicei /metrics)
   - Avantaj: funcționează bine în medii dinamice și containerizate

3. **Componente principale:**
   - **Server Prometheus** - colectează și stochează date time-series
   - **Client libraries** - pentru instrumentarea aplicațiilor
   - **Pushgateway** - pentru acceptarea job-urilor de scurtă durată
   - **Exporters** - pentru expunerea metricilor din sisteme terțe
   - **Alertmanager** - pentru gestionarea alertelor

4. **PromQL:**
   - Limbaj de query puternic pentru interogarea datelor
   - Permite filtrare, agregare și operații pe serii temporale
   - Suportă rate, counter, histograme și alte funcții avansate

5. **Integrare:**
   - Se integrează excelent cu Kubernetes
   - Grafana pentru vizualizări avansate
   - Alertmanager pentru notificări
   - Service discovery pentru identificarea automată a țintelor

**Avantaje:**
- Scalabilitate ridicată
- Reziliență (poate funcționa în condiții de degradare)
- Model de date multidimensional puternic
- Eficient pentru metrici numeroase
- Potrivit pentru arhitecturi microservices și containere

**Limitări:**
- Nu este proiectat pentru logging (deși poate integra sisteme de logging)
- Arhitectura pull poate complica monitorizarea în anumite scenarii
- Retenția pe termen lung necesită soluții adiționale

### 37. Explică conceptul de "logging" și "tracing".
**Răspuns:** Logging și tracing sunt două tehnici fundamentale de observabilitate în sistemele distribuite, fiecare cu roluri distincte dar complementare:

**Logging:**
- **Definiție:** Înregistrarea evenimentelor discrete care apar în cadrul unei aplicații sau sistem
- **Scop:** Captarea stării, erorilor, și evenimentelor din timpul execuției
- **Caracteristici:**
  - Evenimentele sunt de obicei înregistrate ca text structurat sau nestructurat
  - Include timestamp, nivel de severitate, componenta sursă, și mesajul propriu-zis
  - Pot conține informații contextuale adiționale (user, session, request ID)
- **Niveluri tipice:** ERROR, WARN, INFO, DEBUG, TRACE
- **Utilizări:** Debugging, audit, analiza comportamentului, conformitate
- **Unelte:** ELK Stack, Fluentd, Loki, Graylog, Splunk

**Tracing (Distributed Tracing):**
- **Definiție:** Urmărirea unei cereri sau tranzacții pe măsură ce traversează componentele unui sistem distribuit
- **Scop:** Vizualizarea și analiza fluxului de cereri prin microservicii
- **Concepte cheie:**
  - **Span** - o operațiune individuală într-un trace
  - **Trace** - colecția completă de span-uri pentru o singură cerere/tranzacție
  - **Parent-child relationships** - arată dependențele între span-uri
  - **Context propagation** - transmiterea info de trace între servicii
- **Utilizări:** Identificarea bottleneck-urilor, analiza latențelor, debugging sisteme distribuite
- **Unelte:** Jaeger, Zipkin, OpenTelemetry, AWS X-Ray

**Diferențe cheie:**
- **Granularitate:** Logging captează evenimente punctuale, tracing captează fluxul complet prin sistem
- **Contextualizare:** Tracing oferă o imagine de ansamblu a sistemului, logging oferă detalii despre evenimente specifice
- **Volum:** Logging tinde să genereze mai multe date, tracing este mai selectiv

**Cum funcționează împreună:**
- Logging poate fi asociat cu un trace ID pentru a corela loguri cu un trace specific
- Tracing poate conține link-uri către loguri relevante pentru un span
- Împreună cu metricile, formează cele "trei piloni ai observabilității"

**Best practices:**
- Standardizarea formatelor de logging
- Utilizarea de trace IDs în loguri pentru corelație
- Sampling inteligent pentru tracing în sisteme de volum mare
- Centralizarea și indexarea pentru analiză rapidă

### 38. Cum ai configura monitorizarea pentru o aplicație?
**Răspuns:** Configurarea unui sistem de monitorizare eficient pentru o aplicație implică mai mulți pași și considerate pentru a asigura vizibilitate completă asupra performanței și sănătății aplicației:

**1. Strategie și planificare:**
- **Identificarea metricilor critice** - ce trebuie măsurat (latență, throughput, rate de erori, utilizare resurse)
- **Stabilirea SLIs și SLOs** - indicatori și obiective de nivel de serviciu
- **Determinarea nivelurilor de alertare** - ce este critic vs. ce este informativ
- **Stabilirea perioadei de retenție** - cât timp păstrăm datele istorice

**2. Instrumentarea aplicației:**
- **Integrarea bibliotecilor de monitoring** în cod (Prometheus client, OpenTelemetry)
- **Expunerea endpoint-urilor de health** (health checks, readiness, liveness)
- **Implementarea logging-ului structurat** cu niveluri corespunzătoare
- **Adăugarea de tracing** pentru cereri prin sistema distribuit

**3. Colectarea datelor:**
- **Configurarea unui agent de colectare** pe fiecare server/container
- **Setarea job-urilor de scraping** pentru Prometheus
- **Configurarea pipeline-urilor de logging** (Fluentd, Logstash)
- **Setarea exporterilor** pentru sisteme de bază (Node Exporter, cAdvisor)

**4. Stocarea și procesarea:**
- **Configurarea bazelor de date time-series** (Prometheus, InfluxDB)
- **Setarea sistemelor de indexare pentru loguri** (Elasticsearch)
- **Implementarea retenției și arhivării** 
- **Configurarea agregării** pentru a reduce volumul de date

**5. Vizualizare și alertare:**
- **Crearea dashboard-urilor** în Grafana pentru diferite audiențe (dev, ops, management)
- **Configurarea alertelor** pentru condiții anormale
- **Setarea notificărilor** (email, Slack, PagerDuty)
- **Implementarea de playbook-uri** pentru răspuns la alerte comune

**6. Monitorizarea pe straturi:**
- **Infrastructură:** CPU, memorie, disk I/O, rețea
- **Container/runtime:** metrics Kubernetes, utilizare container
- **Aplicație:** latență, rate de erori, request-uri pe secundă
- **Business:** metrici de business (conversii, utilizatori activi)
- **End-user experience:** timpul de încărcare, disponibilitate

**7. Monitorizare proactivă vs. reactivă:**
- **Proactivă:** detectarea tendințelor anormale înainte să devină probleme
- **Reactivă:** detectarea și rezolvarea rapidă a problemelor

**8. Considerații de implementare:**
- Asigurarea monitorizării în toate mediile (dev, test, prod)
- Automatizarea configurării monitoring-ului ca parte din deployment
- Tratarea monitoring-ului ca cod (config versionată, testată, automatizată)
- Implementarea principiului "defense in depth" - multiple straturi de detecție

### 39. Ce este ELK stack sau Elastic stack?
**Răspuns:** ELK Stack (redenumit Elastic Stack) este o colecție de unelte open-source care lucrează împreună pentru a ingesta, procesa, stoca și vizualiza date de logging și metrici în timp real.

**Componentele principale:**

1. **Elasticsearch:**
   - Bază de date distribuită de căutare și analiză bazată pe Lucene
   - Stochează toate datele de log indexate
   - Oferă căutare rapidă, full-text și analiză
   - Scalabilitate orizontală prin adăugarea de noduri

2. **Logstash:**
   - Pipeline de procesare a datelor care ingesta date din multiple surse
   - Transformă și îmbogățește datele (parsing, filtrare, augmentare)
   - Trimite datele procesate către destinații (de obicei Elasticsearch)
   - Suportă numeroase input-uri, filtre și output-uri

3. **Kibana:**
   - Interfață web pentru vizualizarea și interacțiunea cu datele din Elasticsearch
   - Permite crearea de dashboard-uri interactive
   - Oferă capabilități de analiză și vizualizare avansate
   - Include instrumente pentru management și monitorizare

4. **Beats (adăugat ulterior):**
   - Agenți de colectare de date lightweight pentru diverse tipuri de date
   - **Filebeat** - pentru loguri de fișiere
   - **Metricbeat** - pentru metrici de sistem și servicii
   - **Packetbeat** - pentru date de rețea
   - **Winlogbeat** - pentru event logs Windows
   - **Heartbeat** - pentru monitorizarea disponibilității

**Flux de date tipic:**
1. Beats colectează date din surse
2. Logstash procesează și transformă datele (opțional, Beats pot trimite direct la Elasticsearch)
3. Elasticsearch indexează și stochează datele
4. Kibana oferă vizualizare și interacțiune cu datele

**Utilizări comune:**
- Centralizarea și analiza logurilor de aplicații
- Monitorizarea infrastructurii IT
- Detectarea și investigarea incidentelor de securitate
- Business analytics
- Monitorizarea aplicațiilor

**Avantaje:**
- Ecosistem extins cu componente bine integrate
- Foarte scalabil pentru volume mari de date
- Flexibilitate ridicată pentru diverse tipuri de date
- Comunitate activă și documentație bună

**Considerații:**
- Necesită resurse semnificative pentru volume mari de date
- Configurația complexă pentru implementări enterprise
- Costurile de licensing pentru funcționalități avansate (X-Pack)

### 40. Ce metrici sunt importante de urmărit într-un sistem?
**Răspuns:** Metricile importante de urmărit diferă în funcție de componenta sistemului, dar pot fi organizate în câteva categorii-cheie:

**1. Metrici de infrastructură:**
- **CPU:** utilizare, load average, timp în state-uri (user, system, io-wait)
- **Memorie:** utilizare, swap, presiune de memorie
- **Disk:** spațiu utilizat, IOPS, latență, throughput
- **Rețea:** bandwidth, pachete trimise/primite, latență, rate de erori
- **Sistem de operare:** procese, file handles, uptime

**2. Metrici de aplicație:**
- **Disponibilitate:** uptime, health checks
- **Latență:** timpul de răspuns (p50, p90, p99)
- **Throughput:** request-uri pe secundă, tranzacții pe secundă
- **Rata de erori:** erori pe minut, procentaj de erori
- **Saturație:** cozi, thread pools, conexiuni
- **Garbage Collection:** (pentru limbaje precum Java) frecvență și durată

**3. Metrici de baze de date:**
- **Conexiuni:** active, max, timeout-uri
- **Query-uri:** execuții per secundă, durată
- **Cache:** hit rate, dimensiune
- **Lock-uri:** număr, durată, așteptare
- **Indexuri:** utilizare, eficiență

**4. Metrici de container/orchestrare:**
- **Pod/container:** stare, reporniri, resource utilization
- **Orchestrator:** health, resource allocation
- **Deployment:** durată, success rate
- **Autoscaling:** events, resource utilization

**5. Metrici de business/utilizator:**
- **Utilizatori activi:** DAU, MAU, sesiuni concurente
- **Acțiuni:** conversii, achiziții, înregistrări
- **Abonoș:**i ratele de retenție, churn
- **Performanță frontend:** loading time, interactivitate
- **Utilizarea funcționalităților:** care caracteristici sunt folosite

**6. Metrici SLI/SLO:**
- **Availability:** procentaj din timp când sistemul este funcțional
- **Latency:** timpul necesar pentru a servi o cerere
- **Throughput:** volumul de cereri procesate
- **Error rate:** procentajul de cereri care eșuează

**7. Metrici de securitate:**
- **Autentificări:** succese, eșecuri, blocare conturi
- **Scanări de vulnerabilități:** rezultate, tendințe
- **Activitate anormală:** modele de trafic suspecte, acces neautorizat

**Principiile USE și RED:**
- **USE (Utilizare, Saturație, Erori)** - pentru resurse
  - **Utilizare:** procentul de timp când resursa este ocupată
  - **Saturație:** gradul în care resursa are muncă extra
  - **Erori:** numărul de evenimente de eroare

- **RED (Rate, Erori, Durată)** - pentru servicii
  - **Rate:** numărul de cereri per secundă
  - **Errors:** numărul de cereri eșuate
  - **Duration:** timpul necesar pentru procesarea cererilor

### 41. Ce este alerting și cum configurezi alerte eficiente?
**Răspuns:** Alerting este procesul de notificare automată când sistemele monitorizate prezintă comportamente anormale sau problematice care necesită atenție. Scopul este de a identifica și a rezolva problemele înainte ca acestea să afecteze utilizatorii sau să conducă la eșecuri majore.

**Principii pentru alerte eficiente:**

1. **Acționabilitate:**
   - Alertele trebuie să indice probleme care necesită acțiune imediată
   - Evită alertele pentru situații care nu pot fi rezolvate
   - Fiecare alertă ar trebui să aibă un playbook sau următorii pași clari

2. **Reducerea zgomotului:**
   - Evită "alert fatigue" prin eliminarea alertelor false sau redundante
   - Grupează alertele similare sau corelate
   - Implementează de-duplication pentru evitarea alertelor repetate

3. **Contextualizare:**
   - Include informații suficiente pentru diagnosticare rapidă
   - Adaugă link-uri către dashboard-uri relevante sau documentație
   - Oferă detalii despre impact și severitate

4. **Ierarhizare:**
   - Definește niveluri clare de severitate (Critical, Warning, Info)
   - Diferențiază canalele de notificare bazate pe severitate
   - Folosește escaladare pentru alerte nerezolvate

**Cum să configurezi alerte eficiente:**

1. **Definirea condițiilor clare:**
   - Bazate pe SLO/SLI și praguri justificate
   - Condiții suficient de specifice pentru a evita false pozitive
   - Folosește funcții de agregare pentru a reduce zgomotul (avg, sum, rate)

2. **Implementarea duratelor și histerezie:**
   - Alerte triggerate doar când condiția persistă (ex: "CPU > 90% pentru 5 minute")
   - Histerezie pentru a evita "flapping" (revenire rapidă între stări)

3. **Canalele de notificare:**
   - Alege canale potrivite pentru echipă (Slack, Email, PagerDuty, SMS)
   - Diferențiază canalele în funcție de urgență și oră
   - Asigură notificări clare, directe și consistente

4. **Testare și îmbunătățire continuă:**
   - Testează alertele regulat pentru a verifica eficacitatea
   - Revizuiește și refinează pe baza experienței
   - Fă post-mortem pentru incidente și ajustează alertele

**Exemple de unelte de alerting:**
- **Alertmanager** (Prometheus) - pentru gestionarea alertelor din Prometheus
- **Grafana Alerting** - alertare bazată pe dashboard-uri
- **PagerDuty** - pentru on-call management și escaladare
- **OpsGenie** - pentru management de incidente și alertare
- **Nagios Alerts** - din sistemul clasic de monitoring

## Securitate și Best Practices

### 42. Cum integrezi securitatea în DevOps (DevSecOps)?
**Răspuns:** DevSecOps este abordarea care integrează practici de securitate în întregul ciclu de viață DevOps, făcând securitatea o responsabilitate partajată între echipele de dezvoltare, operațiuni și securitate. Scopul este de a implementa securitatea "shift-left" - mai devreme în ciclul de dezvoltare.

**Principii DevSecOps:**
- Securitatea ca și cod
- Automatizarea testării de securitate
- Feedback rapid
- Colaborare strânsă între echipe
- Monitorizare continuă
- Îmbunătățire continuă

**Cum să implementezi DevSecOps:**

1. **Integrare în faza de dezvoltare:**
   - **Analiza statică a codului (SAST)** - scanarea codului pentru vulnerabilități
   - **Code review** cu focus pe securitate
   - **Pre-commit hooks** pentru verificări de securitate
   - **Biblioteci și dependențe securizate**
   - **Secure coding guidelines**

2. **Integrare în pipeline-ul CI/CD:**
   - **Scanare de dependențe** (SCA - Software Composition Analysis)
   - **Scanare de vulnerabilități** pentru imagini container
   - **Testare automată de securitate (DAST)**
   - **Infrastructure as Code security scanning**
   - **Verificare pentru secrets expuse**

3. **Securizarea infrastructure și deployment:**
   - **Hardening** pentru sisteme de operare și container-e
   - **Network segmentation**
   - **Least privilege** pentru toate componentele
   - **Secure configuration management**
   - **Container security** (imagini minimale, non-root users)

4. **Monitorizare și răspuns:**
   - **Runtime security monitoring**
   - **Log analysis** pentru detectarea incidentelor
   - **Vulnerability scanning** continuu
   - **Incident response automation**
   - **Threat intelligence integration**

5. **Governance și compliance:**
   - **Policy as Code** - definirea și verificarea automată a politicilor
   - **Compliance automation** - verificări continue pentru standarde specifice
   - **Security metrics și reporting**
   - **Auditabilitate** în toate etapele

**Unelte populare pentru DevSecOps:**
- **SAST:** SonarQube, Checkmarx, GitHub Advanced Security
- **DAST:** OWASP ZAP, Burp Suite
- **SCA:** Snyk, Dependabot, OWASP Dependency Check
- **Secret scanning:** GitGuardian, Trufflehog
- **Container security:** Trivy, Clair, Anchore
- **IaC security:** Checkov, Terrascan, tfsec
- **Compliance:** InSpec, Open Policy Agent

**Beneficii:**
- Detectarea problemelor de securitate mai devreme când sunt mai ieftine de rezolvat
- Reducerea timpului de remediere
- Îmbunătățirea posturii generale de securitate
- Securitate consistentă în toate mediile
- Reducerea blocajelor cauzate de verificări de securitate manuale

### 43. Ce sunt secretele în DevOps și cum le gestionezi?
**Răspuns:** În contextul DevOps, secretele sunt orice informații sensibile care nu trebuie expuse public și sunt folosite pentru autentificare, autorizare sau criptare. Acestea includ parole, chei API, certificate, token-uri OAuth și chei private.

**Tipuri comune de secrete:**
- Credențiale pentru baze de date
- Chei API pentru servicii externe
- Certificate SSL/TLS
- Token-uri de acces OAuth
- SSH keys
- Chei de criptare
- Credențiale cloud

**Provocări în gestionarea secretelor:**
- Secretele nu trebuie să ajungă în repository-uri de cod
- Rotația periodică a secretelor
- Accesul securizat la secrete de către aplicații
- Audit și trasabilitate
- Compatibilitatea între medii (dev, test, prod)

**Practici și soluții pentru gestionarea secretelor:**

1. **Utilizarea vault-urilor pentru secrete:**
   - **HashiCorp Vault** - soluție completă pentru gestionarea secretelor
   - **AWS Secrets Manager** - pentru mediile AWS
   - **Azure Key Vault** - pentru mediile Azure
   - **Google Secret Manager** - pentru GCP
   - **Kubernetes Secrets** - nativ în Kubernetes (deși are limitări)

2. **Injectarea secretelor la runtime:**
   - Variabile de mediu
   - Montarea secretelor ca fișiere (în K8s)
   - Sidecar patterns pentru preluarea secretelor

3. **Prevenirea expunerii secretelor în cod:**
   - **Git hooks** pre-commit pentru verificarea secretelor
   - **Scanners** pentru detectarea secretelor (GitGuardian, Trufflehog)
   - **Gitignore** pentru fișiere cu secrete
   - Separarea configurației de cod

4. **Automatizarea și Infrastructure as Code:**
   - Injectarea secretelor în timpul deployment-ului
   - Parametrizarea template-urilor
   - Utilizarea serviciilor de parametri (AWS SSM Parameter Store)

5. **Best practices pentru secrete:**
   - **Principiul privilegiului minim** - acces doar la secretele necesare
   - **Rotația automată** a secretelor
   - **Monitoring și alerting** pentru acces la secrete
   - **Audit logging** pentru toate operațiunile cu secrete
   - **Segregarea** secretelor între medii

6. **Integrare cu CI/CD:**
   - Utilizarea secretelor securizate în pipeline-uri (CircleCI Contexts, GitHub Secrets)
   - Limitarea expunerii secretelor doar la joburile care le necesită
   - Izolarea mediilor de build

**Exemple de configurare:**

**HashiCorp Vault:**
```hcl
path "secret/data/application/*" {
  capabilities = ["read"]
}
```

**Kubernetes Secret:**
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secrets
type: Opaque
data:
  db-password: cGFzc3dvcmQxMjM=  # Base64 encoded
```

**Docker Compose cu environment secrets:**
```yaml
services:
  app:
    image: my-app
    environment:
      - DB_PASSWORD_FILE=/run/secrets/db_password
    secrets:
      - db_password
secrets:
  db_password:
    file: ./db_password.txt
```

### 44. Cum implementezi scanarea de vulnerabilități în pipeline-ul CI/CD?
**Răspuns:** Implementarea scanării de vulnerabilități în pipeline-ul CI/CD este o componentă esențială a DevSecOps, permițând detectarea timpurie a problemelor de securitate înainte ca acestea să ajungă în producție.

**Tipuri de scanări de vulnerabilități pentru CI/CD:**

1. **Scanare de cod sursă (SAST - Static Application Security Testing):**
   - Analizează codul sursă pentru vulnerabilități fără a executa aplicația
   - Detectează probleme precum injecții SQL, XSS, CSRF, etc.
   - Unelte: SonarQube, Checkmarx, Fortify, GitHub Code Scanning

2. **Analiza compozițiilor software (SCA - Software Composition Analysis):**
   - Scanează dependențele și bibliotecile third-party pentru vulnerabilități cunoscute
   - Verifică licențele de software pentru a asigura compliance
   - Unelte: OWASP Dependency Check, Snyk, WhiteSource, GitHub Dependabot

3. **Scanare de imagini container:**
   - Verifică imagini Docker pentru vulnerabilități
   - Identifică package-uri OS cu vulnerabilități cunoscute
   - Unelte: Trivy, Clair, Anchore, Docker Scan

4. **Testare dinamică (DAST - Dynamic Application Security Testing):**
   - Testează aplicația în timp ce rulează
   - Simulează atacuri reale pe aplicația funcțională
   - Unelte: OWASP ZAP, Burp Suite, Acunetix

5. **Infrastructure as Code scanning:**
   - Verifică configurațiile IaC pentru probleme de securitate
   - Identifică misconfigurări în Terraform, CloudFormation, etc.
   - Unelte: Checkov, tfsec, Terrascan

**Implementare în pipeline-ul CI/CD:**

1. **Integrare în etapele pipeline-ului:**
   ```yaml
   # Exemplu Jenkins pipeline
   pipeline {
     stages {
       stage('Build') { ... }
       stage('SAST') {
         steps {
           sh 'sonar-scanner'  # Scanare SAST
         }
       }
       stage('SCA') {
         steps {
           sh 'dependency-check --project App --scan ./app'
         }
       }
       stage('Container Scan') {
         steps {
           sh 'trivy image myapp:latest'
         }
       }
       stage('DAST') {
         steps {
           sh 'zap-cli quick-scan --self-contained --start-options "-config api.disablekey=true" http://my-app-staging'
         }
       }
     }
   }
   ```

2. **Gestionarea rezultatelor:**
   - Integrarea rapoartelor de vulnerabilități în dashboard-uri
   - Definirea pragurilor de severitate pentru aprobarea/respingerea build-urilor
   - Generarea de issue-uri pentru vulnerabilități descoperite

3. **Progressive security gates:**
   - Scanări mai ușoare și rapide în etapele timpurii
   - Scanări mai comprehensive pentru branch-urile principale
   - Scanări complete înainte de deployment în producție

4. **Optimizare pentru performanță:**
   - Scanare incrementală unde este posibil
   - Paralelizarea scanărilor pentru a reduce timpul
   - Caching pentru a îmbunătăți viteza

5. **Feedback și remediare:**
   - Raportare clară a vulnerabilităților descoperite
   - Clasificarea și prioritizarea problemelor
   - Indicații pentru remediere
   - Auto-remediere unde este posibil

**Exemplu GitLab CI:**
```yaml
stages:
  - build
  - test
  - security-scan
  - deploy

sast:
  stage: security-scan
  script:
    - gitlab-sast

dependency_scanning:
  stage: security-scan
  script:
    - gitlab-dependency-scan

container_scanning:
  stage: security-scan
  script:
    - gitlab-container-scan

dast:
  stage: security-scan
  script:
    - gitlab-dast
```

**Best practices:**
- Scanează cât mai devreme în pipeline
- Automatizează complet procesul
- Stabilește praguri clare pentru severity
- Planifică remedieri prioritizate
- Integrează rezultatele în procesul de dezvoltare
- Educă dezvoltatorii despre vulnerabilități comune

### 45. Ce înseamnă "least privilege principle" și cum îl aplici?
**Răspuns:** Principiul privilegiului minim (least privilege principle) este un concept fundamental de securitate care stipulează că orice utilizator, proces sau sistem ar trebui să aibă doar privilegiile minime necesare pentru a-și îndeplini funcțiile și nu mai mult.

**Definiție și importanță:**
- Fiecare entitate trebuie să aibă doar accesul necesar pentru a-și îndeplini rolul
- Reduce suprafața de atac și limitează impactul potențial în caz de compromitere
- Este o cerință în numeroase standarde de securitate și compliance (GDPR, PCI-DSS, ISO 27001)

**Cum să aplici principiul privilegiului minim în DevOps:**

1. **Pentru utilizatori și conturi:**
   - Crearea de roluri bine definite cu permisiuni specifice
   - Revizuirea și auditarea periodică a permisiunilor
   - Utilizarea autentificării multi-factor pentru conturi privilegiate
   - Implementarea Just-In-Time (JIT) access pentru privilegii temporare

2. **În cloud și infrastructură:**
   - Utilizarea IAM (Identity and Access Management) cu roluri granulare
   - Implementarea Service Accounts dedicate pentru fiecare aplicație
   - Limitarea IP-urilor care pot accesa resursele sensibile
   - Folosirea boundary services pentru acces la resurse

3. **În containere și Kubernetes:**
   - Rularea containerelor ca utilizatori non-root
   - Utilizarea security contexts pentru a limita privilegiile
   - Implementarea Network Policies pentru a limita comunicarea între pod-uri
   - Folosirea PodSecurityPolicies sau Pod Security Standards

4. **În aplicații:**
   - Implementarea RBAC (Role-Based Access Control) la nivel de aplicație
   - Folosirea unor servicii dedicate pentru operațiuni privilegiate
   - Limitarea accesului la API-uri sensibile
   - Implementarea time-limited tokens pentru operațiuni

5. **În pipeline-uri CI/CD:**
   - Utilizarea credențialelor specific pentru joburi
   - Limitarea permisiunilor pentru service accounts CI/CD
   - Separarea mediilor și pipeline-urilor pentru producție și dezvoltare

**Exemple concrete de implementare:**

**AWS IAM Policy restrictivă:**
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::specific-bucket",
        "arn:aws:s3:::specific-bucket/*"
      ]
    }
  ]
}
```

**Docker security context:**
```yaml
# În Kubernetes
apiVersion: v1
kind: Pod
spec:
  securityContext:
    runAsUser: 1000
    runAsGroup: 3000
    fsGroup: 2000
  containers:
  - name: app
    image: myapp
    securityContext:
      allowPrivilegeEscalation: false
      readOnlyRootFilesystem: true
      capabilities:
        drop:
          - ALL
```

**RBAC în Kubernetes:**
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
```

**Strategii de implementare:**
1. Începe cu **"zero trust"** - niciun acces inițial, adaugă permisiuni specific
2. Folosește **"time-bound access"** - permisiuni temporare
3. Implementează **"break glass"** pentru acces de urgență, cu logging și alerting intensiv
4. Utilizează **"mandatory access control"** unde este posibil
5. Automatizează auditarea și revizuirea permisiunilor

### 46. Care sunt best practices pentru backup și disaster recovery?
**Răspuns:** Backup și disaster recovery (DR) sunt componente esențiale ale unei strategii de reziliență, asigurând că datele pot fi recuperate și serviciile restaurate în caz de eșec sau dezastru.

**Backup Best Practices:**

1. **Strategie 3-2-1:**
   - 3 copii ale datelor
   - Stocate pe 2 medii diferite
   - Cu 1 copie offsite/off-premises

2. **Tipuri de backup:**
   - **Full backup** - copie completă a tuturor datelor
   - **Incremental backup** - doar schimbările de la ultimul backup
   - **Differential backup** - toate schimbările de la ultimul full backup
   - **Snapshot** - captură de moment a stării sistemului

3. **Automatizare:**
   - Backup-uri programate automat
   - Monitorizare a succesului backup-urilor
   - Alertare pentru eșecuri de backup

4. **Testare și verificare:**
   - Testarea regulată a restore-ului din backup
   - Verificarea integrității backup-urilor
   - Simulări de recovery

5. **Securitate:**
   - Criptarea backup-urilor
   - Protecția împotriva ransomware (backup-uri imutabile)
   - Controlul accesului la backup-uri

**Disaster Recovery Best Practices:**

1. **Planificare DR:**
   - **Business Impact Analysis (BIA)** - pentru a înțelege impactul întreruperilor
   - **Recovery Time Objective (RTO)** - timpul maxim acceptabil până la recuperare
   - **Recovery Point Objective (RPO)** - pierderea maximă acceptabilă de date

2. **Strategii DR:**
   - **Backup & Restore** - simplu dar RTO mai mare
   - **Pilot Light** - componente minime mereu active în DR
   - **Warm Standby** - copie scaled-down mereu rulând
   - **Hot Site / Multi-site** - redundanță activă în multiple locații

3. **Automatizare DR:**
   - Scripts de automatizare pentru recovery
   - Infrastructure as Code pentru reconstruirea mediilor
   - Testare automată a procedurilor DR

4. **DR Testing:**
   - Simulări regulate de dezastru
   - Tabletop exercises
   - Game days / chaos engineering

5. **Documentație:**
   - Proceduri pas cu pas pentru diverse scenarii
   - Liste de contacte și escaladare
   - Trigger points pentru activarea planului DR

**Implementare în cloud:**

**AWS:**
- **Backup:** AWS Backup, S3 cu Lifecycle Policies, AMIs, Snapshots
- **DR:** Multi-AZ, Multi-Region, Route 53 failover, CloudFormation pentru recovery

**Azure:**
- **Backup:** Azure Backup, Azure Storage replication
- **DR:** Azure Site Recovery, Availability Zones, Traffic Manager

**GCP:**
- **Backup:** Persistent Disk snapshots, Cloud Storage
- **DR:** Regional/multi-regional resources, Deployment Manager

**Implementare pentru baze de date:**
- **Replicare:** Sync sau async
- **Point-in-Time Recovery:** Din transaction logs
- **Database mirroring / Always On:** Pentru high availability

**Implementare pentru Kubernetes:**
- **Velero:** Pentru backup-ul clusterelor K8s
- **Multi-cluster deployments:** Folosind tools precum ArgoCD
- **StatefulSet backups:** Volumele persistente trebuie backup-uite separat

**Exemple de IaC pentru DR (Terraform):**
```hcl
# Configurare multi-region cu AWS
provider "aws" {
  region = "us-west-2"  # Primary region
  alias  = "primary"
}

provider "aws" {
  region = "us-east-1"  # DR region
  alias  = "dr"
}

# Resources in primary region
resource "aws_instance" "primary" {
  provider      = aws.primary
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

# Resources in DR region
resource "aws_instance" "dr" {
  provider      = aws.dr
  ami           = "ami-0915bcb5fa77e4892"
  instance_type = "t2.micro"
}

# Route53 failover configuration
resource "aws_route53_health_check" "primary" {
  provider          = aws.primary
  fqdn              = "primary.example.com"
  port              = 80
  type              = "HTTP"
  resource_path     = "/"
  failure_threshold = 3
  request_interval  = 30
}

resource "aws_route53_record" "www" {
  zone_id = "Z1234567890"
  name    = "www.example.com"
  type    = "A"
  
  failover_routing_policy {
    type = "PRIMARY"
  }
  
  set_identifier = "primary"
  health_check_id = aws_route53_health_check.primary.id
  alias {
    name                   = "primary.example.com"
    zone_id                = "Z1234567890"
    evaluate_target_health = true
  }
}
```

## Situații practice

### 47. Descrie cum ai seta un pipeline CI/CD pentru o aplicație web.
**Răspuns:** Setarea unui pipeline CI/CD pentru o aplicație web implică crearea unui flux automatizat pentru build, testare și deployment. Iată cum aș aborda acest proces:

**1. Planificarea pipeline-ului:**

Analize ce tehnologii folosește aplicația web:
- Front-end: JavaScript/TypeScript, framework (React, Angular, Vue)
- Back-end: Node.js, Python, Java, etc.
- Bază de date: MySQL, PostgreSQL, MongoDB
- Infrastructură: Kubernetes, serverless, VMs

**2. Configurarea source control:**
- Repository Git (GitHub, GitLab, Bitbucket) cu branching strategy
- Protecții pentru branch-ul principal (code reviews, approvals)
- Pull/Merge request templates

**3. Alegerea uneltei de CI/CD:**
- GitHub Actions, GitLab CI, Jenkins, CircleCI, Azure DevOps

**4. Definirea etapelor pipeline-ului:**

**Etapa de Integrare (CI):**
```yaml
# Exemplu GitHub Actions workflow
name: CI Pipeline

on:
  push:
    branches: [ develop, feature/* ]
  pull_request:
    branches: [ main, develop ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Lint code
        run: npm run lint
      
      - name: Run unit tests
        run: npm test
      
      - name: Build application
        run: npm run build
      
      - name: Run SAST scan
        uses: github/codeql-action/analyze@v2
      
      - name: Run dependency scanning
        run: npm audit
      
      - name: Build and push Docker image
        if: github.event_name != 'pull_request'
        uses: docker/build-push-action@v3
        with:
          context: .
          push: true
          tags: myapp:${{ github.sha }}
```

**Etapa de Continuous Delivery (CD):**
```yaml
# Exemplu de deployment workflow
name: CD Pipeline

on:
  workflow_run:
    workflows: ["CI Pipeline"]
    branches: [develop]
    types: [completed]

jobs:
  deploy-staging:
    if: ${{ github.event.workflow_run.conclusion == 'success' }}
    runs-on: ubuntu-latest
    environment: staging
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Kubernetes CLI
        uses: azure/setup-kubectl@v3
      
      - name: Deploy to Staging
        run: |
          kubectl apply -f k8s/staging/
          kubectl set image deployment/myapp myapp=myapp:${{ github.sha }}
      
      - name: Run integration tests
        run: npm run test:integration
      
  deploy-production:
    needs: deploy-staging
    runs-on: ubuntu-latest
    environment: production
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Kubernetes CLI
        uses: azure/setup-kubectl@v3
      
      - name: Deploy to Production
        run: |
          kubectl apply -f k8s/production/
          kubectl set image deployment/myapp myapp=myapp:${{ github.sha }}
      
      - name: Run smoke tests
        run: npm run test:smoke
```

**5. Configurarea mediilor:**
- **Development** - pentru testare continuă
- **Staging/QA** - mediu similar cu producția pentru testare
- **Production** - mediul live

**6. Implementarea deployment strategies:**
- **Blue/Green Deployment** - două medii identice, switch între ele
- **Canary Deployments** - release gradual către un subset de utilizatori
- **Rolling Updates** - înlocuirea instanțelor pe rând

**7. Monitoring și feedback:**
- Integrarea metricilor de performanță (APM)
- Alertare pentru eșecuri de deployment
- Logging și monitoring post-deployment
- Feature flags pentru controlul funcționalităților

**8. Securitate în pipeline:**
- Scanare de vulnerabilități
- Analiză statică de cod (SAST)
- Scanare de imagini Docker
- Secret management

**9. Automatizarea infrastructurii:**
- Infrastructure as Code (Terraform, CloudFormation)
- Kubernetes manifests sau Helm charts
- Integrarea IaC în pipeline

**10. Documentarea procesului:**
- README pentru procesul de CI/CD
- Troubleshooting guides
- Rollback procedures

**Pentru aplicații complexe, aș adăuga:**
- Testare de performanță automatizată
- Analiză de calitate a codului (SonarQube)
- Deployment approval workflows
- Integrare cu management de release

### 48. Cum ai aborda depanarea unei aplicații care nu funcționează în producție?
**Răspuns:** Depanarea (troubleshooting) unei aplicații care nu funcționează în producție necesită o abordare metodică și sistematică. Iată procesul pe care l-aș urma:

**1. Evaluarea inițială și colectarea informațiilor:**

- **Verificarea alertelor și monitoring:**
  - Ce alerte s-au declanșat?
  - Care sunt metricile afectate (latență, error rate, etc.)?
  
- **Determinarea impactului:**
  - Este afectat tot sistemul sau doar o componentă?
  - Câți utilizatori sunt afectați?
  - Este intermitent sau constant?

- **Timeline al incidentului:**
  - Când a început problema?
  - Au existat modificări recente (deployments, config changes)?

**2. Stabilizarea imediată (dacă e necesar):**

- **Considerarea unui rollback:**
  ```bash
  # Rollback la versiunea anterioară în Kubernetes
  kubectl rollout undo deployment/my-app
  ```

- **Scalarea resurselor** dacă e o problemă de capacitate:
  ```bash
  # Scalare rapidă pentru a gestiona load-ul
  kubectl scale deployment my-app --replicas=10
  ```

- **Activarea circuit breakers** pentru a izola componentele problematice

**3. Investigare sistematică:**

- **Verificarea logurilor aplicației:**
  ```bash
  # Vizualizarea logurilor în timp real
  kubectl logs -f deployment/my-app
  # sau în Elastic Stack
  # căutarea erorilor în perioada relevantă
  ```

- **Verificarea stării resurselor:**
  ```bash
  # Verificarea statusului pod-urilor
  kubectl get pods
  
  # Descrierea detaliată a unui pod cu probleme
  kubectl describe pod my-app-pod-12345
  ```

- **Verificarea networking:**
  ```bash
  # Testarea conectivității
  kubectl exec -it my-app-pod -- curl -v database-service:5432
  
  # Verificarea DNS
  kubectl exec -it my-app-pod -- nslookup database-service
  ```

- **Verificarea resurselor sistemului:**
  ```bash
  # Utilizarea CPU/memorie
  kubectl top pods
  ```

- **Verificarea dependențelor externe:**
  - Sunt serviciile externe (APIs, b