---
title: 'Procédure pas à pas : Appel d’API Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: d2dc80ec689f3e9fd2f36c36c3847ec4e5d1a576
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783158"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Procédure pas à pas : Appel d’API Windows (Visual Basic)
Les API Windows sont des bibliothèques de liens dynamiques (DLL) qui font partie du système d’exploitation Windows. Elles permettent d’effectuer des tâches lorsqu’il est difficile d’écrire des procédures équivalentes de votre choix. Par exemple, Windows fournit une fonction nommée `FlashWindowEx` qui permet d’effectuer la barre de titre pour une application alternez entre clairs et foncés.  
  
 L’avantage d’utiliser les API Windows dans votre code est qu’ils peuvent enregistrer des temps de développement, car ils contiennent des dizaines de fonctions utiles qui sont déjà écrit et prêtes à être utilisées. L’inconvénient est que les API de Windows peut être difficile de travailler avec et envoyés lorsque des problèmes surgissent.  
  
 Les API Windows représentent une catégorie spéciale d’interopérabilité. Les API Windows n’utilisent pas de code managé, n’ont pas intégrées bibliothèques de types et utiliser des types de données qui sont différents de ceux utilisés avec Visual Studio. Raison de ces différences, et étant donné que les API Windows ne sont pas des objets COM, l’interopérabilité avec les API Windows et le .NET Framework est effectué à l’aide de code non managé, ou PInvoke. Code non managé est un service qui permet au code managé appelle des fonctions non managées implémentées dans des DLL. Pour plus d’informations, consultez [consommation de fonctions DLL non managées](../../../framework/interop/consuming-unmanaged-dll-functions.md). Vous pouvez utiliser PInvoke dans Visual Basic à l’aide du `Declare` instruction ou en appliquant la `DllImport` attribut à une procédure vide.  
  
 Appels d’API de Windows ont été une partie importante de Visual Basic de programmation dans le passé, mais sont rarement nécessaires avec Visual Basic .NET. Autant que possible, vous devez utiliser le code managé à partir de .NET Framework pour effectuer des tâches, au lieu d’appels d’API de Windows. Cette procédure pas à pas fournit des informations pour les cas dans lesquels l’utilisation des API de Windows est nécessaire.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Déclarent des appels d’API à l’aide de  
 La méthode la plus courante d’appeler les API de Windows est à l’aide de la `Declare` instruction.  
  
### <a name="to-declare-a-dll-procedure"></a>Pour déclarer une procédure DLL  
  
1. Déterminer le nom de la fonction que vous souhaitez appeler, ainsi que ses arguments, les types d’arguments et retourner une valeur, ainsi que le nom et l’emplacement de la DLL qui la contient.  
  
    > [!NOTE]
    >  Pour obtenir des informations complètes sur les API Windows, consultez la documentation du SDK Win32 dans l’API de Windows Platform SDK. Pour plus d’informations sur l’une des constantes qui utilisent les API Windows, examinez les fichiers d’en-tête tels que Windows.h inclus avec le SDK de plateforme.  
  
2. Ouvrez un nouveau projet d’Application de Windows en cliquant sur **New** sur le **fichier** menu, puis en cliquant sur **projet**. La boîte de dialogue **Nouveau projet** s’affiche.  
  
3. Sélectionnez **Windows Application** dans la liste des modèles de projet Visual Basic. Le nouveau projet s’affiche.  
  
4. Ajoutez le code suivant `Declare` fonctionner à la classe ou le module dans lequel vous souhaitez utiliser la DLL :  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Parties de l’instruction Declare  
 La `Declare` instruction inclut les éléments suivants.  
  
#### <a name="auto-modifier"></a>Modificateur Auto  
 Le `Auto` modificateur indique au runtime de convertir la chaîne en fonction du nom de méthode en fonction des règles du common language runtime (ou nom d’alias si spécifié).  
  
#### <a name="lib-and-alias-keywords"></a>Mots clés lib et Alias  
 Le nom qui suit le `Function` mot clé est le nom de votre programme utilise pour accéder à la fonction importée. Il peut être le même que le nom réel de la fonction que vous appelez, ou vous pouvez utiliser n’importe quel nom de procédure valide et l’emploient puis le `Alias` mot clé pour spécifier le nom réel de la fonction que vous appelez.  
  
 Spécifiez le `Lib` mot clé, suivi par le nom et l’emplacement de la DLL qui contient la fonction que vous appelez. Vous n’avez pas besoin de spécifier le chemin d’accès pour les fichiers situés dans les répertoires de système de Windows.  
  
 Utilisez le `Alias` mot clé si le nom de la fonction que vous appelez n’est pas un nom de procédure Visual Basic valid ou est en conflit avec le nom d’autres éléments dans votre application. `Alias` Indique le véritable nom de la fonction appelée.  
  
#### <a name="argument-and-data-type-declarations"></a>Argument et les déclarations de Type de données  
 Déclarez les arguments et leurs types de données. Cette partie peut être difficile, car les types de données qui utilise Windows ne correspondent pas aux types de données de Visual Studio. Visual Basic effectue une grande partie du travail pour vous en convertissant les arguments en types de données compatibles, un processus appelé *marshaling*. Vous pouvez contrôler explicitement la façon dont les arguments sont marshalés en utilisant le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut défini dans le <xref:System.Runtime.InteropServices> espace de noms.  
  
> [!NOTE]
>  Les versions précédentes de Visual Basic vous permettent de déclarer des paramètres autorisaient `As Any`, ce qui signifie que des données de toutes les données type peut être utilisé. Visual Basic requiert que vous utilisez un type de données spécifique pour toutes les `Declare` instructions.  
  
#### <a name="windows-api-constants"></a>Constantes de l’API de Windows  
 Certains arguments sont des combinaisons de constantes. Par exemple, le `MessageBox` API indiqué dans cette procédure pas à pas accepte un argument entier appelé `Typ` qui contrôle comment la boîte de message s’affiche. Vous pouvez déterminer la valeur numérique de ces constantes en examinant le `#define` instructions dans le fichier WinUser.h. Les valeurs numériques sont généralement affichés au format hexadécimal, vous pouvez donc utiliser une calculatrice pour les ajouter et convertir en nombre décimal. Par exemple, si vous souhaitez combiner les constantes pour le style d’exclamation `MB_ICONEXCLAMATION` 0 x 00000030 et la valeur Oui/aucun style `MB_YESNO` 0 x 00000004, vous pouvez ajouter les nombres et obtenir un résultat de 0 x 00000034, ou 52 décimales. Bien que vous pouvez utiliser le résultat décimal directement, il est préférable de déclarer ces valeurs en tant que constantes dans votre application et de les combiner à l’aide de la `Or` opérateur.  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>Pour déclarer des constantes pour les appels d’API de Windows  
  
1. Consultez la documentation de la fonction Windows que vous appelez. Déterminer le nom de l’une des constantes qu’il utilise et le nom du fichier .h qui contient les valeurs numériques pour ces constantes.  
  
2. Utilisez un éditeur de texte, tel que le bloc-notes, pour afficher le contenu du fichier d’en-tête (.h) et rechercher les valeurs associées aux constantes que vous utilisez. Par exemple, le `MessageBox` API utilise la constante `MB_ICONQUESTION` pour afficher un point d’interrogation dans la boîte de message. La définition de `MB_ICONQUESTION` dans WinUser.h et est comme suit :  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Ajouter équivalent `Const` instructions pour votre classe ou module pour rendre ces constantes disponibles pour votre application. Par exemple :  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>Pour appeler la procédure DLL  
  
1. Ajoutez un bouton nommé `Button1` au démarrage de l’écran pour votre projet, puis double-cliquez dessus pour afficher son code. Le Gestionnaire d’événements pour le bouton s’affiche.  
  
2. Ajoutez le code pour le `Click` Gestionnaire d’événements pour le bouton que vous avez ajouté pour appeler la procédure et de fournir les arguments appropriés :  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. Exécutez le projet en appuyant sur F5. La boîte de message s’affiche avec les deux **Oui** et **non** boutons de réponse. Cliquez sur l’une.  
  
#### <a name="data-marshaling"></a>Marshaling de données  
 Visual Basic convertit automatiquement les types de données des paramètres et valeurs de retour pour les appels d’API de Windows, mais vous pouvez utiliser le `MarshalAs` attribut pour spécifier explicitement les types de données non managée qui attend une API. Pour plus d’informations sur le marshaling d’interopérabilité, consultez [Marshaling d’interopérabilité](../../../framework/interop/interop-marshaling.md).  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Pour utiliser Declare et MarshalAs dans un appel d’API  
  
1. Déterminer le nom de la fonction que vous souhaitez appeler, ses arguments, les types de données, et la valeur de retour.  
  
2. Pour simplifier l’accès à la `MarshalAs` d’attribut, ajoutez un `Imports` instruction au début du code pour la classe ou un module, comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. Ajouter un prototype de fonction pour la fonction importée à la classe ou le module que vous utilisez et appliquez le `MarshalAs` aux paramètres d’attribut ou la valeur de retour. Dans l’exemple suivant, un appel d’API qui attend le type `void*` est marshalé en tant que `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Appels d’API à l’aide de DllImport  
 Le `DllImport` attribut fournit une deuxième méthode permettant d’appeler des fonctions dans les DLL sans bibliothèques de types. `DllImport` équivaut à peu près à utiliser un `Declare` instruction mais offre davantage de contrôle sur la façon dont les fonctions sont appelées.  
  
 Vous pouvez utiliser `DllImport` avec la plupart des API Windows appelle tant que l’appel fait référence à un partage (parfois appelé *statique*) méthode. Vous ne pouvez pas utiliser des méthodes qui requièrent une instance d’une classe. Contrairement aux `Declare` instructions, `DllImport` appels ne peut pas utiliser le `MarshalAs` attribut.  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Pour appeler une API Windows à l’aide de l’attribut DllImport  
  
1. Ouvrez un nouveau projet d’Application de Windows en cliquant sur **New** sur le **fichier** menu, puis en cliquant sur **projet**. La boîte de dialogue **Nouveau projet** s’affiche.  
  
2. Sélectionnez **Windows Application** dans la liste des modèles de projet Visual Basic. Le nouveau projet s’affiche.  
  
3. Ajoutez un bouton nommé `Button2` vers le formulaire de démarrage.  
  
4. Double-cliquez sur `Button2` pour afficher le code du formulaire.  
  
5. Pour simplifier l’accès aux `DllImport`, ajoutez un `Imports` instruction au début du code pour la classe de formulaire de démarrage :  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Déclarez une fonction vide qui précède le `End Class` instruction pour le formulaire et le nom de la fonction `MoveFile`.  
  
7. Appliquer le `Public` et `Shared` modificateurs pour la déclaration de fonction et définir les paramètres pour `MoveFile` basée sur les arguments de la fonction de l’API de Windows utilise :  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Votre fonction peut avoir n’importe quel nom de procédure valide ; le `DllImport` attribut spécifie le nom de la DLL. Il gère également le marshaling d’interopérabilité pour les paramètres et l’API utilise des types de valeurs de retour, vous pouvez donc choisir les types de données de Visual Studio qui sont similaires aux données.  
  
8. Appliquer le `DllImport` d’attribut à la fonction vide. Le premier paramètre est le nom et l’emplacement de la DLL contenant la fonction que vous appelez. Vous n’avez pas besoin de spécifier le chemin d’accès pour les fichiers situés dans les répertoires de système de Windows. Le deuxième paramètre est un argument nommé qui spécifie le nom de la fonction dans l’API Windows. Dans cet exemple, le `DllImport` attribut force les appels à `MoveFile` peut être envoyé à `MoveFileW` dans KERNEL32. DLL. Le `MoveFileW` méthode copie un fichier à partir du chemin `src` pour le chemin d’accès `dst`.  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Ajoutez le code pour le `Button2_Click` Gestionnaire d’événements pour appeler la fonction :  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Créez un fichier nommé Test.txt et placez-le dans le répertoire C:\Tmp sur votre disque dur. Créez le répertoire Tmp si nécessaire.  
  
11. Appuyez sur F5 pour démarrer l'application. Le formulaire principal s’affiche.  
  
12. Cliquez sur **Button2**. Le message « le fichier a été déplacé avec succès » s’affiche si le fichier peut être déplacé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Création de prototypes dans du code managé](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Marshaling d’un délégué comme méthode de rappel](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
