
# **ADA** 

<a id="Sommaire"></a>
## SOMMAIRE 

- <a href="#Packages"> Packages </a>
- <a href="#Typage"> Typage </a>
- <a href="#Declaration"> Déclaration (procédure et fonction)</a>
- <a href="#Fonctions"> Fonctions de bibliothèques </a>
- <a href="#Mots_cles"> Mots clés </a>
- <a href="#Operateurs"> Opérateurs </a>
- <a href="#boucles"> Boucles </a>
- <a href="#Composite"> Les composites </a>
- <a href="#Enum"> Les enumérations </a>
- <a href="#structData"> Les structures de données </a>
- <a href="#pointeur"> Les pointeurs </a>
- <a href="#Exemple_de_code"> Exemple de code </a>
// Mettre un menu.
- <a href="#Note"> Notes </a>
- <a href="#Erreur"> Erreur compilateur GNAT </a>


<a id="Packages"></a>
## <a href="#Sommaire">Packages : </a>
  - Ex : `Ada.text_io`.
  <a id="Insertion_package_Up"></a>
  - Insertion d'un package (ou Context Clause) :
    - `with` : Insère.
    -  `use` : Utilise. 
    - Ex. : <a href="#Insertion_package">lien</a>

  - Liste :
    - `ada.text_io` :  
      - Affiche chaîne de caractères (fc° put()).
    - `ada.integer_text_io` : 
      - Affiche les entiers et les entiers naturel (fc° put()).
    - `ada.float_text_io` : 
      - Ajout de variable de type float.
    - `ada.numerique` : 
      - Utilisation de pi e.
    - `ada.numerics.elementary_functions` : 
      - Fonction mathématique.
    - `ada.characters.handling` : 
      - Modifier la casse. 
    - `Ada.Strings.Unbounded` : 
      - Créer une chaîne non contrainte (taille illimité). 
    - `Ada.Directories` :
      - Gestion des fichiers et répertoires.
    - `Ada.Strings.Fixed` :
      - Manipule des chaînes de type String (taille fixe).
    - etc . . .

<a id="creationPackage_Up"></a>
- Création de package :
  - Créer fichiers : 
    - `.ads` (correspond au .h en C) :
        - On met type, variable qui seront utilisé dans procédure. 
        - Ex. : <a href="#CreationPackage">lien.</a>
    - `.adb` (correspond au .c du)


<a id="Typage"></a>
## <a href="#Sommaire">Typage : </a>
  - `Integer` : les entier signés (peuvent être négatif).
  - `Natural` : les entier non signés.
   0 est compté comme un positif.
  - `Float` : nb à virgule (peuvent être positif ou négatif).
  - `Character` : lettre (`'a'`, `'B'`, etc).
  - `Boolean` : 
    - afficher en valeur numérique :
      ```ada
      put(Integer'IMAGE(Boolean'POS(a)));
      ```

<a id="Declaration"></a>
## <a href="#Sommaire">Déclaration : </a>

  <a id="Procedures_Up"></a>
  - Procédure : 
    ``` ada
    procedure MyFonction is  
      -- Déclaration des variables.  
    begin
      -- Les instructions. 
    end MyFonction ;
    ```
    - Note : 
      - Ce déclare dans la procédure principale, au même endroit que les variables.
      - Attention si une procédure est utilisé, placé sa déclaration avant, sinon la procédure principale ne la connaîtra pas.
      - Ne retourne aucun résultat.
      - Spécification de la procédure : <br>
      Ex. :  <a href="#Procedures_Code">lien</a>
    - Ex. : <a href="#Procedures_Code">lien</a>

  - Fonctions :
    ```ada
    function MyFunction(...) return float is
    begin
      ...
      return ...,
    end MyFunction;
    
    ```

<a id="Fonctions"></a>
## <a href="#Sommaire">Procédures des bibliothèques : </a>

  - `put()` : 
    - Affiche une chaîne de cara ou un cara.<br>
      Package : `text_io`.       
    - Affiche un entier. <br>
    Package : `integer_text_io`.
    
  - `put_line()` : 
    - Affiche chaîne de cara ou un cara + saut de ligne. <br>
  Package : `integer_text_io`.
  
  <a id="skip_line_Up"></a>
  - `get()` : récupère la saisie clavier.
    - Ex. : get(age); la variable age récupère la saisie utilisateur (peut être une chaîne de cara. ou un cara. ou un entier ou un float).
    - Note : tjrs mettre <a href="#skipe_line">skipe_line</a> après.
  
  - `get_line()` : récupère la saisie clavier.
    - Paramètres :
      - Item (type : string) : récupère une chaîne de cara.
      - Last (type : natural): longueur de la chaîne saisie au clavier (vaudra au maximum la taille de la chaîne déclarée).
    
    - Notes : 
      - Fait un skipe_line auto si Last < taille de la chaîne déclarée.
      - Si Last = taille de la chaîne déclarée on devra ajouté manuellement skipe_line.
        - Ex. : 
          ```ada 
          procedure mySaisie is
            txt : string(1..10); -- 10 est la taille de la chaîne déclarée.
            lgString : natural;
          begin
            get_line(txt, lgString);
            if lgString = txt'length then
              skipe_line;
            end if;
            -- Affiche la longueur de la chaîne entré.
            put_line(text(1..lgString));
          end mySaisie;
          ```
  - `get_line()` : récupère un cara. ou une chaîne dans un fichier.
    - Paramètres :
      - File (type File_Type) : le nom du fichier.
      - Item (type String) : récupère un cara. ou une chaîne.
      - Last (type natural) : taille de la chaîne récupérée.

  - `integer()` : float to integer. Convertit un float en integer.
  
  - `float()` : integer to float. Convertit un integer en float.
  
  - `integer'image(1);` : convertit un integer en string.
  
  - `integer'value("salut");` : convertit un string en integer.

<a id="Mots_cles"></a>
## <a href="#Sommaire">Mots clés : </a>

  - `new_line` : saut de ligne.
  
  - `with` : Dit quel package on veut utilisé.
  
  - `use` : Appel le package qu'on veut utilisé.
  
  - `procedure` : début de la fonction qui précéde son nom. Ex. : procedure MaFction.
  
  - `is` : début du corps de la fonction. C'est ici qu'on met les déclarations.
  
  - `begin` : Commencement des instructions.
  
  - `end` : Fin de la fonction. Sert aussi de fin de bloc de déclaration.
  
  - `Width =>` : Supprime les espaces à gauche lors d'un affichage. Ex. : put(10, Width => 0); Ici,
  Supprime tout les espaces.
  
  - `Exp =>` (Exposant) : supprime l'exposant lors de l'affichage. Ex. : put(1.85, Exp => 0)
  
  - `Aft =>` (after) : précise le nb de chiffre après la virgule. Ex. put(1.85, Exp => 0, Aft => 0);

  <a id="skipe_line"></a>
  - <a href="#skip_line_Up">↑</a> `skip_line` : ce place tjrs après get.
    -  Pour :
        - Sauté le cara. de fin de ligne.
        - Vider le buffer clavier.
  
  - `constant` : empêche la modification de la variable.
  
  - `declare` : déclare une variable temporaire ; supprimer à la fin du bloc de déclaration `end`.<br> `declare` peut être déclaré comme pour les variable. Ex. : `Bloc_Declaration : declare`.

  - `'base` : représente le type de base d'un autre type ou sous-type. Attribut utilisé pour accéder à une valeur d'un type de base.
    - Ex. :
      ```ada
      procedure main is

      type ET_Base is (ET_Base_First, A, B, C, ET_Base_Last);
      subtype ET is ET_Base range A .. C;
      E : ET'base := ET_Base'First;
      begin
        -- On affiche ET_Base_First avec E. Si pas 'Base impossible.
       put(ET'image(E)); 
      end main;
      ```
  - `charactere` : sert à la déclaration d'un caractère. Ex. : cCara : character := 'K';
    - Attribut pour table ASCII :
        - `'first` : Renvoie le 1er caractère.
        - `'last` : Renvoie le dernier caractère.
        - `'pos(...)` : Position du charactère. Renvoie un integer.
        - `'val(...)` : Renvoie le n-ième caractère. Entre les parenthèse doit être un integer.
        - `'succ(...)` : Renvoie le caractère suivant.
        - `'pred(...)` : Renvoie le caractère précédent.
        &nbsp;Ex. : 
          ``` ada
            c := character'last;
            n := character'pos('z');
            c := character'val(165);
          ```
    - Package Standard (type Character):
      - Permet d'utiliser les caractères ASCII. <br>
        - Ex. : 
        ```ada
        put("Un saut de ligne : " & ASCII.LF);
        ```
        - Lien : https://en.wikibooks.org/wiki/Ada_Programming/Libraries/Standard/Apex  

  - `**` : Puissance. Ex. : 5**2 = 25.
  - `mod` : Pour modulo.
  - `if` : condition.
  - `then` : pour afficher le contenu du if.
  - `else` : si if à échouer on fait autre chose.
  - <a id="condition_multiples_Up"></a>Conditions multiples : 
    - `case` : pour utiliser des conditions multiple.
    - `when` :  s'utilise avec `case` test un cas. 
    - `=>` : après le cas pour indiquer ce qui doit être fait.
    - `others` : s'utilise avec `case` quand tous les autres tests ont échoués. Obligatoire sinon erreur du compilateur.<br>
    Ex. : <a href="#condition_multiples">lien</a>

  - <a id="boucle_up"></a>Boucles : 
    - `loop` : début.
    - `end loop` : fin. 
    - `when` : quand.
    - `while` : tant que ... on continue. 
    - `for` : même chose que `while` mais avec un compteur sur la même ligne.<br>
      - `reverse` : compte à l'envers.
    - `exit` : pour arrêté une boucle for, while...
    - Ex. :  <a href="#boucle">lien</a>
  
  - <a id="goto_up"></a>Instruction goto : 
    - Ex. :  <a href="#goto">lien</a>

  - Paramètre des procédures et fonctions :
    - Si ils sont :
      - `in` : paramètre d'entré (lecture). On peut le lire mais pas le modifié.
      - `out` : paramètre de sortie (écriture). On peut le modifier mais pas le lire.
    - Note : on peut combiné les 2 `in out`.
  
  

<a id="Operateurs"></a>
## <a href="#Sommaire">Opérateurs : </a>
- Comparaison : <br>
  - &nbsp; `=` &nbsp; "égal à". <br> 
  - `/=` &nbsp; "différent de". <br>
  - &nbsp; `<` &nbsp; "plus petit que". <br> 
  - &nbsp; `>` &nbsp; "plus grand que". <br> 
  - `<=` &nbsp; "inférieur ou égale à". <br> 
  - `>=` &nbsp; "plus grand ou égale à". <br> 

- <a id="Booleen_up"></a>Les opérateurs booléens : 
  - `Not` : non
  - `and` : et
  - `or`  : ou
  - `xor` : ou exclusif (les 2 arguments ne peuvent pas être vrai ensemble).
  - Autre notation :
    - `|` : or (s'utilise avec case. Ex. : <a href="#Booleen">lien</a>).
    
- <a id="Ope_Appart_Up"></a>Appartenance : <br>
`in` "dans". <br>
`range` "intervalle". Pour parcourrir tous les éléments d'un tableau. Intervalle de 1 à la fin du tableau.<br>
Ex. : <a href="#Ope_Appart">lien</a>

<a id="boucles"></a>
## <a href="#Sommaire">Boucles : </a>
  - `for in` : boucle normal.
    ```ada
      for i in 1..10 loop
        put(i); new_line;
      end loop;
    ```

  - `for of` : s'applique à tous les éléments du tableau. <br>
  Ex. : 
    ```ada
      procedure MyProcedure is
        type Tableau is Array(1..8) of integer;
        MyArray : tableau := (7,8,9,10,11,12);
      begin
        -- Pour chaque element de MyArray.
        for elem of MyArray loop
          elem := elem + 1;
        end loop;
      end MyProcedure;
    ```
    Note : `for of` s'applique aussi à des tableau de dimension > 1 (un seul `for of` suffit).

  - `while` :
    ```ada
      while nb /= 0 loop
        nb := nb -1;
      end loop;
    ```

  - Expression quantifiées :
    - `for all` : quantificateur universel. Sert que pour les expressions quantifiers. Parcour le tableau pour y effectuer des tests.<br>
    Ex. :
      ```ada
        ...
          nValPositif : boolean;
        begin
          ...
          -- Si une seul valeur de MyArray est négatif => nValPositif = false.
          nValPositif := (for all i in MyArray'range => MyArray(i) > 0);
          ...
          -- Avec un for of :
          nValPositif := (for all elem of MyArray => elem > 0);
      ```

  - Quantificateur existentiel :
    - `for some` : si il existe un seul élément on continue.<br>
      Ex. :
      ```ada
        -- Tant que un elem est <= 0, => on ajoute 1 a tous les elements du tableau.
        While (for some elem of MyArray => elem <= 0) loop
          for elem of MyArray loop
            e := e + 1;
          end loop;
        end loop;
      ```


<a id="Composite"></a>
## <a href="#Sommaire">Les composites : </a>

  <a id="menu"></a>
  ## <center>Menu</center>
  
  - Tableau : 
    - <a href="#tab_Declaration">Déclaration.</a>
    - <a href="#tab_Affectation">Affectation global.</a>
    - <a href="#tab_Attr">Attribut.</a>
    - <a href="#tab_2dim">Tableau à 2 dimenssion.</a>
    - <a href="#tab_redim">Tableau redimenssionnable.</a>
    - <a href="#tab_AffectationTranche">Affectation par tranche.</a>
    - <a href="#tab_DeclarationDansProg">Déclarer un tableau en cours de programme.</a>

  - Chaîne de caractère :
    - <a href="#String_Declaration">Déclaration.</a>
    - <a href="#String_AffectationGlobal">Affectation global.</a>
    - <a href="#String_Manipulation">Manipulation.</a>
    - <a href="#String_Casse">Modifier la casse.</a>
    - <a href="#String_Concat">Concaténation.</a>
    - <a href="#String_VariableTostring">Transformer une variable en string.</a>
    - <a href="#String_StringToNum">Transformer une string de nombres/chiffres en valeur numérique.</a>
    - <a href="#String_ASCII_toNum">Transformer une lettre en sa valeur numérique.</a>
    - <a href="#String_compar">comparaison de strings.</a>
    - <a href="#String_SaisieClavier">Saisie au clavier.</a>
    - <a href="#String_NonContrainte">Chaîne de caractère non contrainte.</a>

  <br><br>

  - Def. : manipulation d'objets plus complexe qu'une variable.
  - Types composites :
     <a id="tableau"></a>
    - <a href="#Composite">↑</a> Le tableau : `array`.

      <a id="tab_Declaration"></a>
      - <a href="#menu">↑</a> Déclaration :
        ```ada 
        type tableau is array (1..5) of integer;
        MyArray : tableau;
        ```
        ```ada 
        type index is range 1..5;

        type tableau is array (index) of natural;
        MyArray : tableau;
        ```
        
        ```ada
        type MyInt is range 1..10;
        type index is range 1..5;

        type tableau is array (index) of MyInt;
        MyArray : tableau;
        ```

      
      <a id="tab_Affectation"></a>
      - <a href="#menu">↑</a> Affectation global :
        - Liste :
          ```ada
            procedure main is
              tailleMax : constant natural := 5;
              type tableau is array (1..tailleMax) of integer;
              MyArray : tableau;
            begin
              MyArray := (1,2,3,4,5,6);
            end main;
          ```
        - Agrégat :
          ```ada
            MyArray := (0|2 => 17, other => 0)
          ```
        - Valeur :
          ```ada
            MyArray(1) : 1;
            MyArray(2) : 2;
            ...
          ```
        - Boucle :
          ```ada
            for i in 1..5 loop
              MyArray(i) := 0;
            end loop
          ```
      
      <a id="tab_Attr"></a>
      - <a href="#menu">↑</a> Attributs : 
        - `MyArray'range`
          ```ada
            for i in MyArray'range loop
              MyArray(i) := 0;
            end loop;
          ```
          Note : `MyArray'range` indique l'interval de numérotation des case du tableau.

        - `MyArray'first` : renvoi le 1er indice du tableau `MyArray`.
          ```ada
            put(MyArray'first);
          ```
        - `MyArray'last` : idem mais le dernier.
          ```ada
            put(MyArray'last);
          ```
        - `MyArray'length` : donne la longueur du tableau.
        - `MyArray(MyArray'first)` : récupére la valeur de la case.
   
      <a id="tab_2dim"></a>
      - <a href="#menu">↑</a> Tableau à 2 dimenssions :
        - Prototype :
          ```ada       
            type MyArray is array(1..2,1..5) of natural;
          ```
          Intervalles :
          - 1..2 : nb de lignes.
          - 1..5 : nb de colonnes.

        - Initialisation :
          - Liste :
            ```ada
              MyArray := ((1,2,3,4,5,0), (10, 11, 12, 13, 14, 15));
            ```
          - Boucle :
            ```ada
              for i in 1..2 loop
                for j in 1..5 loop
                  MyArray(i, j) := 0;
                end loop;
              end loop;
            ```
          - Agrégat :
            ```ada
            -- Ligne 1 que des 0.
            -- Idem ligne 2.
            MyArray := (1 => (0,0,0,0), 2 =>(0,0,0,0));
            -- ou :
            MyArray := (1..2 => (0,0,0,0));
            -- ou :
            MyArray := (1..2 => (1..4 => 0));
            ```
      
      <a id="tab_redim"></a>
      - <a href="#menu">↑</a> Tableau redimenssionnable (ou type non-contraint) :
        ```ada
          type MyArray is array(integer range <>) of natural;
        ```
        Note : 
          - les types ne sont pas contraint, mais les objets de type MyArray le sont.
          - Ex. : 
            ```ada
              MyArrayNoContraint : MyArray(1..8);
            ```
      
      <a id="tab_AffectationTranche"></a>
      - <a href="#menu">↑</a> Affectation par tranche :
        ```ada
          MyArray_1 : tableau(1...10);
          MyArray_2 : tableau(1...6);
          MyArray_3 : tableau(1...4);

          MyArray_1(1..6) := MyArray_2;
          MyArray_1(1..10) := MyArray_3;
        ```
        Note : impossible avec des tableaux > 1.
      
      <a id="tab_DeclarationDansProg"></a>
      - <a href="#menu">↑</a> Déclarer un tableau en cours de programme :
      ```ada
        procedure main is 
          n : integer;
          type MyArray is array (integer range <>) of integer;
        begin
          put("Quelle est la longueur du tableau");
          get(n); skip_line
          declare
            tab : MyArray(1..n);
          begin
            ...
          end;
        end main;
      ```  
      Note : objet MyArray supprimer à la fin du `end`.

    <a id="chaineCara"></a>
    - <a href="#Composite">↑</a> La chaine de 
    caractère : 
      
      <a id="String_Declaration"></a>
      - <a href="#menu">↑</a> Déclaration et/ou initialisation :
        - Note : obligation de mettre le nb de cara. de la taille max de la chaîne déclaré.
        
        - Ex. :
          ```ada
          procedure myString is
            txt : string(1..10);
            txt2 : string(1..10) := "Salut     "; -- 10 cara. obligatoire.
          begin
            txt := "Salut     "; -- 10 cara. obligatoire.
          end myString;
          ```
        
        - Restriction :
          ```ada
          procedure myString is
            A : String; -- Déclaration illégale.
          begin 
            A := "world";
          end;
          ```

      <a id="String_AffectationGlobal"></a>
      - <a href="#menu">↑</a> Affectation global :
        ```ada
          with ada.text_io;
          use  ada.text_io;

          procedure manipString is
            txt : string(1..6);
          begin
            txt := "Salut";
          end manipString;
        ```
        ou :
        ```ada
          with ada.text_io;
          use  ada.text_io;

          procedure manipString is
            txt : string(1..6) := "Salut !"
          begin
            ...
          end manipString;
        ```
        ou encore :
        ```ada
          with ada.text_io;
          use  ada.text_io;

          procedure manipString is
            txt : string := "Salut !"
          begin
            ...
          end manipString;
        ```
      
      <a id="String_Manipulation"></a>
      - <a href="#menu">↑</a> Manipulation
        (Se manipule comme les tableaux) : <br>
        - Ex. : 
          ```ada
            with ada.text_io;
            use  ada.text_io;

            procedure manipString is
              txt : string(1..7) := "Salut !"
              -- On doit déclarer à partir de 1 et non de 0.
              idx : natural := 0;
            begin
              put(txt(idx));
            end manipString;
          ```
        - Utilisation des slices :
          ```ada
            procedure ManipString is
              txt : string := "Bonjour !"
            begin
              txt(4..7) := "soir";
            end manipString;
          ```
    
      <a id="String_Casse"></a>
      - <a href="#menu">↑</a> Modifier la casse.
        - Package : Ada.characters.handling
        ```ada
          -- Met en majuscule.
          txt(1..7) := to_upper(txt(1..7));
          -- Met en minuscule.
          txt(1..7) := to_lower(txt(1..7));
        ```
      
      <a id="String_Concat"></a>
      - <a href="#menu">↑</a> Concaténation :
        ```ada
          procedure concate is
            myName : string := "luke".
          begin
            put_line("1 - " & myName);
          end concate;
        ```
        Attention : 
        ```ada
          procedure concate is
            txt : string := "salut".
            myName : string := "luke".
          begin
            -- ceci donnera une erreur car txt est trop petite.
            txt := txt & myName;
          end concate;
        ```
      
      <a id="String_VariableTostring"></a>
      - <a href="#menu">↑</a> Transformer une variable en string :
        ```ada
          integer'image(1);
          float'image(1.05);
        ```
      <a id="String_StringToNum"></a>
      - <a href="#menu">↑</a> Transformer une string de nombres/chifres en valeur numérique :
        ```ada
          integer'value("1");
          float'value("1.05");
        ```

      <a id="String_ASCII_toNum"></a>      
      - <a href="#menu">↑</a> Transformer une lettre en sa valeur numérique :
        ```ada 
          Character'Value('a');
        ```

      <a id="String_compar"></a>
      - <a href="#menu">↑</a> Comparaison de strings :
        - Insensible à la casse.
      Renvoie `false` ou `true`.
        ```ada
          procedure myCompare is
            txt1 : string := "avion";
            txt2 : string := "bus";
          begin
            if txt1 > txt2
              then ...

          end myCompare;
        ```

      <a id="String_SaisieClavier"></a>
      - <a href="#menu">↑</a> Saisie au clavier :
        ```ada
          with Ada.Text_IO;
          use Ada.Text_IO;
          
          procedure Main is
            Str    : String (1 .. 80);
            Taille : Natural;
          begin
            -- Attention : pas de skip_line car le fait implicitement.
            Get_Line (Str, Taille);
            put("taille de pStr" & natural'image(size_pStr_used)); New_Line
            Put (Str); New_Line;
          end Main;
        ```

        ```ada
        -- Si on entre pas de paramètres.
          txt := get_line;
        ```
        Attention :
          - La longueur de la chaîne est inconnue. Possibilité d'erreur.

        ```ada
          procedure main is
            pStr :  string(1..10);
          begin
            get(pStr); -- Attention obligation de rentrer 10 caractère.
          end main;
        ```

      <a id="String_NonContrainte"></a>
      <a id="string_non_contrainte_up"></a>
      - <a href="#menu">↑</a> Chaîne de caractère non contrainte :

        ```ada
          procedure myString is
            txt : unbounded_string;
          begin
            ...
          end myString;
        ```
        Note   : unbounded ne crée pas un tableau, mais une liste vide. 

        Note 2 : il faut faire une conversion de la chaîne avec la fonction `to_unbounded_string()` pour obtenir un unbounded.
        
        Et `to_string()` pour l'inverse.



        Ex. : <a href="#string_non_contrainte">lien</a>

<a id="Enum"></a>
## <a href="#Sommaire">Les énumération : </a>

  - Déclaration :
  ```ada
    type myEnum is (nom1, nom2, ...)
  ```

  - Utilisation des attributs :
    - `'first` : 1er de la liste.
    - `'last` : dernier.
    - `'succ` : suivant.
    - `'pred` : précédent.
    - `'pos` : position du nom.
    - `'val(1)` : donne le nom à la position 1.
    - `'image(nom1)` : crée une str nom1.

  <a id="enumCode_up"></a>
  - Ex. : <a href="#enumCode">lien</a>

<a id="Exemple_de_code"></a>
## <a href="#Sommaire">Exemple de code : </a>

## <center>Menu</center>
<a id="Insertion_packages"></a>
- <a href="#Insertion_packages">Insertion de packages.</a>

<a id="ExPackage"></a>
- <a href="#CreationPackage">Création package.</a>

- <a href="#Procedures">Procédures.</a> 

- <a href="#Fonctions">Fonctions.</a> 

- <a href="#Bloc_declaration">Bloc de déclaration.</a> 

- <a href="#condition_multiples">Condition.</a> 

- <a href="#Ope_Appart">Opérateur 
d'appartenance.</a>

- <a href="#condition_multiples">Conditions multiples.</a>

- <a href="#Simplification_condition">Simplification d'une condition.</a>

- <a href="#Booleen_case">Booléen avec case.</a>

- <a href="#Boucles">Boucles.</a> 

- <a href="#goto">goto.</a> 

- <a href="#Imbrication_fonction_procedure">Imbrication de fonction et/ou procédure.</a>

- <a href="#Valeur_defaut_procedure">Valeur par défaut d'une procédure.</a>

- <a href="#String_non_contrainte">String non contrainte.</a>

- <a href="#enumCode">Énumération</a>


## <center>Code<enter>

- <a id="Insertion_package" href="#Insertion_package_Up">↑</a> Insertion de packages : <br>
  ```ada
    with 
      ada.text_io,
      ada.integer_text_io,
      ada.float_text_io;
    use
      ada.text_io,
      ada.integer_text_io,
      ada.float_text_io;
  ```

- <a id="CreationPackage"></a>
  <a href="#creationPackage_Up">↑</a> ou <a href=#Exemple_de_code>Menu code</a>
  Création de packages : <br>
    - myPackage.ads :
      ```ada
          package myPackage is
            
            type;
            procedure;
            function;

          end integer_array;
      ```
    - myPackage.adb :
      ```ada
        -- with ... ;
        -- use  ... ;

        package body myPackage is
          procedure une_procedure is
            ...
          begin
            ...
          end une_procedure;
        end myPackage; 
      ```
    - Procedure principale :
      ```ada
        with myPackage;
        use  myPackage;

        procedure main is
          ...
        begin
          ...
        end main;
      ```
- <a id="Procedures_Code"></a>
<a href="#Procedures_Up">↑</a>
 Procédures :
  ```ada
  -- Spécification de la procédure.
  -- Note : pas obligé d'avoir de paramètre.
  procedure MyFunction(nVar : natural ; 
                       nVar1 : natural ;
                       nVar2 : character ;
                       nVar3 : boolean ;
                       nVar4 : boolean ;
                       nVar5 : boolean
  );
  ```

  ```ada 
    -- Procédure principale du programme.
    procedure Main is -- Main : nom de la procédure.
      -- Ici on met déclarations et initialisations (affectations).
    begin
      -- Ici on met les instructions.
    end Main; Fin de la procédure.
  ``` 
  
  ```ada 
  -- Sans paramètres.
  procedure main is
    procedure MyProcedure is
      -- Déclaration des variables.
    begin
      -- Les instructions.
    end MyProcedure;
  begin
    MyProcedure; -- procedure sans parametre.
  end main;
  ```
  ```ada
  -- Avec 1 paramètre.
  procedure main is
    procedure MyProcedure(nb : natural) is
      ...
    begin
      ...
    end MyProcedure
  begin
    MyProcedure(10);
  end main;
  ```

  ```ada
  -- Avec plusieurs paramètre.
  procedure main is
    procedure MyProcedure(nb : natural ; nValue : float) is
      ...
    begin
      ...
    end MyProcedure
  begin
    MyProcedure(10, 30);
  end main;
  ```  

- Fonctions : <br>
  ```ada  
    function MyFonction(nVal : natural ; nVal2 : natural) return natural is
      nTotal : natural;
    begin
      nTotal := nVal * nVal2;
      return nTotal;
    end A_Rect; 
  ```

- Bloc de déclaration :
  ```ada
    procedure Mon_Programme is
    begin
      
      Bloc_Numero1 : declare
        --Ici on met déclarations et initialisations
      begin
        --Ici on met les instructions.
      end Bloc_Numero1; 

      Bloc_Numero2 : declare
        --Ici on met déclarations et initialisations
      begin
        --Ici on met les instructions.
      end Bloc_Numero2; 

    end Mon_Programme;
  ```

- Condition :
  - Complexe (`if` et `else if` obligation d'avoir un `end if`): <br>
  ```ada
    if Reponse = 'o'
      then Put("...");
    else if Reponse = 'n'
      then Put("..."); 
    else if Reponse = 'p'
      then Put("...");
    else 
      Put("...");
    end if ; 
    end if ; 
    end if ;
  ```

  - Simplifier (le `elsif` remplace le `else if` donc plus d'obligation d'associé le `end if` avec le `elsif`) : <br>
  ```ada
    if Reponse = 'o' 
      then Put("..."); 
    elsif Reponse = 'n' 
      then Put("...");  
    elsif Reponse = 'p' 
      then Put("..."); 
    else Put("..."); 
    end if;
  ```

- <a id="Ope_Appart" href="#Ope_Appart_Up">↑</a> Opérateur d'appartenance : <br>
  ```ada
    -- Affiche i allant de 1 à la taille du tableau. 
    for i in MyArray'range loop
      put(i); new_line;
    end loop;
  
    if variable in 14..25 --(if variable est compris entre 14 et 25)
  ``` 

- <a id="condition_multiples" href="#condition_multiples_Up">↑</a> ou <a href="#Exemple_de_code">Menu code</a> Conditions multiples :
  ```ada
    case Reponse is
      when '...' => Put("....");
      when '...' => Put("....");
      when '...' => Put("....");
      when '...' => Put("....");
      when others => Put("....");
    end case;
  ```
- Simplification d'une condition :
  ```ada
    nVal := (if Reponse = 'o' then 1 else 0);
    nVal := (if Reponse = 'o' then "lol" else "Pas lol");
    nVal := (if Reponse = 'o' then "lol" elsif Reponse = "lol_2" then "lolus" else "Pas lol");
    nVal := (case Reponse is 
             when 'o' => 1
             when 'n' => 0
             when others => 2);
    x := (if x >= 0 then x else -x);
  ```

- <a id="Booleen" href="#Booleen_up">↑</a> Booléen avec case :
  ```ada
  case Reponse is
    when 'o' | 'O' => put("....");
    when other => put("...");
  end case;
  ```

- <a id="boucle" href="#boucle_up">↑</a> Boucles : 
  ```ada
  loop
    if compteur = nb
      then exit;
    else put("salut");
    end if
  end loop

  loop
    exit when compteur /= nb;
      put_line("...");
    compteur := compteur +1;
  end loop;

  maBoucle : loop
    exit maBoucle when Nb /= 0;
    Nb := Nb -1;
  end loop : maBoucle;

  while nb /= 0 loop
    nb := nb -1;
  end loop;

  for i in 1..nb loop
    -- On s'arrète quand i à atteint nb.
  end loop;

  -- Boucle allant du dernier au 1er élément.
  for i in reverse 1..nb loop
    -- On s'arrète quand i arrive à 1.
  end loop;
  ```

- <a id="goto" href="#goto_up">↑</a> goto :
  ```ada
    <<debut>> 
    if compteur <= nb -- On met une condition sinon on rentre dans une boucle infinie.
      then put("...");
      compteur := compteur +1;
      goto debut;
    end if;
  ```

- Imbrication de fonction et/ou procédure :
  ```ada
    Put(MyFunction(MyVar, MyVar2));
  ```
- Valeur par défaut d'une procédure :
  ```ada
    -- Evitera d'avoir à  mettre une valeur en paramètre.
    Procedure MyProcedure(nVal : natural := 1) is

    begin;
      ...
    end MyProcedure;
  ```

  - Spécifié le paramètre auquel on attribue une valeur :
  ```ada
    val1 := 1; val2 := 2;
    MyProcedure(val1, val2, afficheVal => true);
  ```

- <a id="string_non_contrainte"></a>
<a href="#string_non_contrainte_up">↑</a> String non contrainte :
  ```ada
    ...
    procedure MyStrUnbounded;
      txt : unbounded_string;
    begin
      -- Convertit une string en unbounded.
      txt := to_unbounded_string("salut !");
      -- Convertit un unbounded en string.
      put(to_string(txt));
    end MyStrUnbounded;
  ```

- <a id="enumCode"></a>
<a href="#enumCode_up">↑</a> Énumération :
  ```ada
    procedure main is
      type myEnum is (name1, name2, name3);
    begin
    -- Affiche nom1.
    put(myEnum'image(name1));
    end main;
  ```

<a id="Note"></a>
<a href="#Sommaire">Notes : </a>
- Ada est un langage Polymorphe. Plusieurs fct peuvent avoir le même nom si elles sont dans des packages différents. Pour lui indiqué de quel package la fct provient on écrit : `Ada.Text_IO.Put()`. Sinon on utilise les mots clés `with` et `use`.

- Ada ne tient pas compte "case sensitive" pour les words key. Idem pr les tabulations ou espaces, 1 ou + ne chge rien.

- Ada ne prend pas en charge les accents et caractères spéciaux.

- Ada n'accepte pas les commentaire sur une ligne après un code. Message d'erreur : statement expected.

- Prédicat : question posée attendant une réponse.

- Paramètres :
  - Effectif : 
    - paramètres avec lesquels la fonction/procédure est effectivement appelée.
  - Formel : 
    - Arguments de la fonction/procédure. 

<a id="Erreur"></a>
<a href="#Sommaire">Erreur : </a>

- warning: "unreachable code" : portion de code qui ne sera jamais exécutée.

