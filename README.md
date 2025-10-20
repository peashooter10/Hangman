Link Google Colab
https://colab.research.google.com/drive/1E6CSayV_w88Qzgdem_IWxm1LCsL_nRWu

# Hangman

RULARE

Codul sursă se rulează la apelul funcției run() care apelează celelalte funcții ale programului. În urma rulării programului, se generează cu fișier CSV care conține informații referitoare la rularea codului.

FORMAT I/O

Codul sursă are ca INPUT un fișier CSV care are indicele cuvântului de ghicit, cuvântul de ghicit și indiciul inițial. La final, ca și OUTPUT, se generează un fișier CSV.

DEFINIȚII

Programul Hangman conține mai multe funcții care se combină pentru a ghici un cuvânt.

CODUL SURSĂ ȘI EXECUȚIA ACESTUIA/DEMO

Funcția run() este funcția principală.
  1) Se validează datele de intrare, se citește fișierul și se extrag cuvântul de ghicit(word) și indiciul(pattern).
  2) Datele sunt introduse în funcția joc_hangman() care ghicește cuvântul
  3) Procesul se repetă, iar datele aferente procesului de ghicire sunt scrise într-un fișier CSV.

Funcția joc_hangman() are rolul de a ghici un cuvânt, având ca parametri cuvântul care trebuie ghicit și indiciul inițial.
  1) Se definesc numărul de încercări, grup9-grupul de litere care se creează în funcția grupuri_de_doua_trei_patru_litere(), iar apoi se intră în bucla while până la ghicirea unui cuvânt.
  2) Se apelează funcția lungime_minimă() care furnizează pozițiile literelor necunoscute și distanța minimă intre acestea și o literă cunoscută.
  3) După aceasta se apelează funcția analiză() care returnează punctul care are cei mai mulți vecini cunoscuți.
  4) Apoi se apelează funcția sugestie() care dă o alegere.
  5) După ghicirea cuvântului se apelează funcția grupuri_de_doua_trei_patru_litere() ce are ca scop găsirea unor combinații frecvente de litere pentru comparare și sugerarea unei variante optime(se caută din 2 în 2, 3 în 3 sau 4 în 4 literele vecine care au o sumă cât mai mică, echivalând invers proporțional cu frecvența acestora- sumă mică, frecvență mare- iar apoi grup9 sea ctualizeaz pentru a oferi din ce în ce mai multe variante de alegere).
  6) Procesul se reia în funcția run() pentru toate cuvintele.
     
Funcția sugestie() oferă o variantă optimă.
  1) Se apelează funcția vector_vecini() și se retrunează o listă ce vecinii punctului cu cei mai mulți vecini cunoscuți.
  2) Se creează un șablon care va fi folisit pentru a compara grupul de litere vecini și variantele de litere des utilizate.
  3) Lista opțiuni este creată după apelul funcției asemănări()
  Funcția asemănări() primește șablonul, iar apoi compară șablonul cu grupurile de litere existente într-o oridne bazată pe probabilitatea întâlnirii unui grup de litere ( de exemplu, se caută mai întâi grupuri de tipul cvc, apoi vvv, întrucât este mai probabil ca într-un cuvânt să fie o consoană urmată de o vocală ș invers deât să fie trei vocale consecutive).
  4) Se apelează funcția următoarea_alegere() care, pe baza fecvenței unei litere în limba română, alege o literă.

DEMO
Cuvânt: citronadele; Indiciu: ******ad***
Încercare curentă: ******ad***
Poziție optimă: 10
Litera sugerată: e
Încercare curentă: ******ade*e
Poziție optimă: 9
Litera sugerată: i
Încercare curentă: *i****ade*e
Poziție optimă: 9
Litera sugerată: r
Încercare curentă: *i*r**ade*e
Poziție optimă: 2
Litera sugerată: n
Încercare curentă: *i*r*nade*e
Poziție optimă: 4
Litera sugerată: t
Încercare curentă: *itr*nade*e
Poziție optimă: 4
Litera sugerată: o
Încercare curentă: *itronade*e
Poziție optimă: 9
Litera sugerată: u
Încercare curentă: *itronade*e
Poziție optimă: 9
Litera sugerată: l
Încercare curentă: *itronadele
Poziție optimă: 0
Litera sugerată: c
Cuvântul citronadele a fost ghicit din 9 încercări.


