# Memòria Aplicació Login

- Sobre el codi de les activitats:

    - Indica com accedeixes als diferents elements de la interficie

       Desde el MainActivity accedixc als elements:
       - "imageView" : Creant una variable amb el nom "image" de clase ImageView, i cridant al métode findViewById al que se li proporciona com a argument l'identificador (R.id.imageView) i retorna la seua vista corresponent, en este cas la imatge logoapp.
       - "editTextUsername" : Creant una variable amb el nom "nomIntroduit" de clase EditText, i cridant al métode findViewById al que se li proporciona com a argument l'identificador (R.id.editTextUsername) i retorna la seua vista corresponent, en este cas un camp d'edició de text per a introduir l'usuari.
       - "editTextPassword" : Creant una variable amb el nom "contraIntroduida" de clase EditText, i cridant al métode findViewById al que se li proporciona com a argument l'identificador (R.id.editTextPassword) i retorna la seua vista corresponent, en este cas un camp d'edició de text per a introduir la contraeña.
       - "textViewAttempts" : Creant una variable amb el nom "viewIntents" de clase TextView, i cridant al métode findViewById al que se li proporciona com a argument l'identificador (R.id.textViewAttempts) i retorna la seua vista corresponent, en este cas els intents de login fets a la app.
       - "btLogin" :Creant una variable amb el nom "botoLogin" de clase Button, i cridant al métode findViewById al que se li proporciona com a argument l'identificador (R.id.btLogin) i retorna la seua vista corresponent, en este cas un botó de login.

    - Indica com has realitzat la navegació entre una activitat i altra
      
      Desde el MainActivity he invocant a l'activitat MainScreen creant una variable de nom "intent" i de clase Intent, al constructor d'aquesta li he proporcionat com a primer argument l'activitat d'origen, es a dir el MainActivity i com a segon argument l'activitat MainSreen que es a la que vuic navegar. Seguidament he invocat al métode starActivity passant-li la variable "intent". 


- Sobre el fitxer manifest, investiga el següent:

    - Quantes activitats apareixen configurades? Mostra-les i indica les principals diferències entre elles i què signifiquen.
    
        Apareixen configurades dos activitats: MainActivity i MainScreen.
        Les principal diferencies al fitxer manifest entre una activitat i altra serien que l'activitat MainScreen no té cap intent-filter a diferencia de l'activitat MainActivity, i també que el "android:exported" en el MainScreen esta a fals i en el MainActivity esta a true.


     ~~~
        <activity
               android:name=".MainScreen"
               android:exported="false">
              <meta-data
                 android:name="android.app.lib_name"
                    android:value="" />
            </activity>
            <activity
                android:name=".MainActivity"
                android:exported="true">
                <intent-filter>
                    <action android:name="android.intent.action.MAIN" />

                    <category android:name="android.intent.category.LAUNCHER" />
                </intent-filter>

                <meta-data
                    android:name="android.app.lib_name"
                    android:value="" />
            </activity>
    ~~~

    - Observal’atribut android:exported en elles i investiga en la documentació d’Android què significa i quines repercusions té el seu valor en l’aplicació.

        Significa que si es "true" qualsevol app pot accedir a l'activitat i es pot iniciar amb el nom de classe exacte.
        Si és "false", l'activitat només es pot iniciar amb components de la mateixa aplicació, aplicacions amb el mateix ID d'usuari o components del sistema amb privilegis. Aquest és el valor per defecte quan no hi ha filtres d'intents

- Sobre les traduccions realitzades:

    - Examina la carpeta dels recursos de tipus String,tant en la vista d’Android com en la vista dels fitxers del projecte. Hi ha nous fitxers, carpetes o recursos? Quin nom tenen i què contenen cadascun? 
    
        Si examines la carpeta "strings" desde la vista d'Android apareixen 3 fitxers amb el mateix nom, pero dos d'ells tenen l'icono d'una bandera d'Espanya i al costat del nom en gris "(ca-rES)" i "(es-rES)", pero si ho examines enla vista dels fitxers s'han creat dos carpetes "values-es-rES" i "values-ca-rES" dins de cadascuna hi ha un fitxer "strings.xml" que conte:

        ~~~
        <resources>
        <string name="app_name">LoginApp</string>
        </resources>
        ~~~


