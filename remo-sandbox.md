Title         : 2. gyakorlat
Heading Base  : 2
Doc class     : [reprint,nocopyrightspace]sigplanconf.cls
Author        : Rendszermodellezés

Package       : pgfplots
Package       : tikz
Tex Header    : \usetikzlibrary{arrows,automata,trees,calc,shadings,shapes.geometric,shapes.gates.logic.US,positioning,backgrounds,fit,datavisualization,datavisualization.formats.functions}

<style>
ol ol { list-style: lower-alpha; }
</style>

[TITLE]

# Modellezés alapok

1. Háromrétegű kiszolgáló infrastruktúránk viselkedésének modellezésére megfelelő állapotpartíciók-e a következők: 
    1. \{Webszerver, Alkalmazásszerver, Adatbázisszerver\}
    2. \{Webszerver dolgozik, Alkalmazásszerver dolgozik, Adatbázisszerver dolgozik\}
    3. \{Leállítva, Tétlen üzemel, Aktívan dolgozik\}
    4. $\mathbb{N}$ (mint a pillanatnyilag feldolgozás alatt álló kérések száma)
    5. \{A kérés feldolgozása még nem kezdődött el, a szerverek épp dolgoznak a kéréssel, a kérés kiszolgálása befejeződött\}
    6. \{igaz\}
2. Közlekedési lámpát vezérlő elektronikát tervezünk.
    1. Készítsd el egy egyszerű háromfényű piros--sárga--zöld közlekedési lámpa olyan állapotpartícióját, amely kellően finom ahhoz, hogy a lámpák vezérlését ez alapján lehessen végezni! Győződj meg arról, hogy az állapotpartíció kizárólagos és teljes!
    2. A három égőnek külön-külön mi az állapottere? Milyen absztrakciós viszony áll fent a lámpa és az egyes égők állapottere közt? Hogy viszonyul a lámpa állapottere a három állapotváltozó   direkt szorzatához?
    3. Mik az érvényes állapotátmeneti szabályok? Készítsd el az állapotgráfot!
    4. A piros jelzés végén van egy olyan időszak, amikor a merőleges gyalogosátkelő zöld lámpája már villog. Finomítsuk úgy az állapotgráfot, hogy ez az állapot elkülöníthető legyen!
    5. Amikor a lámpa elektromos fogyasztását vizsgáljuk, csak az érdekel, hogy a három égőből hány ég egyszerre. Absztraháld az állapotgépet úgy, hogy az állapotokat csak a fogyasztásuk különböztesse meg! 
3. Modellezzük állapotgéppel egy mobiltelefon érintőképernyőjére tervezett virtuális billentyűzetet! A billentyűzeten egyszerre vagy a kisbetűk, vagy a nagybetűk, vagy a számok és fontosabb szimbólumok, vagy ritkább szimbólumok láthatóak. Az elsődleges üzemmódváltó gomb a betűk és a számok/szimbólumok beírása között vált, a másodlagos üzemmódváltó pedig ezen kategóriákon belül. Létezik továbbá egy olyan nagybetűs állapot is, amely egy betű leütése után automatikusan kisbetűsre vált. Vegyük figyelembe a bal felső gombot (`q`/`Q`/`1`/`=`), ill. a két üzemmódváltó gombot mint inputot, és a szövegmezőbe begépelt karaktereket mint outputot!
4. Egy összetett állapotgépnek 10 állapotváltozója van, egyenként 4 állapottal. Legfeljebb mekkora a teljes állapottér?
5. Tekintsük az $M_1$ szintetikus állapotgépet!
    1. Determinisztikus-e a viselkedésmodell? Hozzávehető-e, ill. elhagyható-e egyetlen állapotátmeneti szabály, hogy ez megváltozzon?
    1. Absztraháld az állapotgépet $\{a,b\} \rightarrow d$ állapotabsztrakcióval! Hány lehetőség van?
    1. Finomítsd az állapotgépet $a \rightarrow \{e,f\}$ állapotfinomítással! Hány lehetőség van?
    1. Absztraháld az állapotgépet $\{0,1\} \rightarrow w$ tokenabsztrakcióval! Hány lehetőség van?
    1. Finomítsd az állapotgépet $z \rightarrow \{z_1,z_2\}$ tokenfinomítással! Hány lehetőség van?
6.  Készítsd el az azonos input csatornát olvasó $M_1$ és $M_2$ állapotgépek...
    1. ...szinkron szorzatát!
    1. ...aszinkron szorzatát!

$M_1$ állapotgép:

~ Snippet
\begin{tikzpicture}[->,>=stealth',shorten >=1pt,auto,node distance=2.8cm,semithick]
  \tikzstyle{every state}=[]

  \node[initial,state] (A)                    {$a$};
  \node[state]         (C) [below right=of A] {$c$};
  \node[state]         (B) [above right=of C] {$b$};

  \path (A) edge [loop below]    node {$1/y$} ()
        (A) edge                 node {$0/x$} (B)
        (B) edge [bend right=40] node {$1/y$} (A)
        (B) edge [bend right=40] node {$0/-$} (C)
        (C) edge                 node {$0/z$} (A)
        (C) edge [bend right=40] node {$1/z$} (B)
        (C) edge [loop below]    node {$-/z$} ()
        ;
\end{tikzpicture}
~

$M_2$ állapotgép:

~ Snippet
\begin{tikzpicture}[->,>=stealth',shorten >=1pt,auto,node distance=2.8cm,semithick]
  \tikzstyle{every state}=[]

  \node[initial,state] (G)              {$g$};
  \node[state]         (H) [right=of G] {$h$};

  \path (G) edge [bend left=60] node {$1/-$} (H)
        (G) edge [bend left]    node {$0/-$} (H)
        (H) edge []             node {$0/-$} (G)
        (H) edge [bend left]    node {$1/-$} (G)
        (H) edge [bend left=60] node {$1/p$} (G)
        ;
\end{tikzpicture}
~