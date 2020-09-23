---
title: 'Procédure pas à pas : Appel des API Windows'
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
ms.openlocfilehash: 88b3df2f18add6641d0355d2c605bc5f74dabbc7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098318"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Procédure pas à pas : appel des API Windows (Visual Basic)

Les API Windows sont des bibliothèques de liens dynamiques (dll) qui font partie du système d’exploitation Windows. Vous les utilisez pour effectuer des tâches lorsqu’il est difficile d’écrire vos propres procédures équivalentes. Par exemple, Windows fournit une fonction nommée `FlashWindowEx` qui vous permet de faire en sorte que la barre de titre d’une application alterne entre les tons clairs et foncés.  
  
 L’avantage de l’utilisation des API Windows dans votre code est qu’ils peuvent économiser du temps de développement, car ils contiennent des dizaines de fonctions utiles qui sont déjà écrites et en attente d’utilisation. L’inconvénient est que les API Windows peuvent être difficiles à utiliser et Unforgiving en cas de problème.  
  
 Les API Windows représentent une catégorie spéciale d’interopérabilité. Les API Windows n’utilisent pas de code managé, n’ont pas de bibliothèques de types intégrées et utilisent des types de données différents de ceux utilisés avec Visual Studio. En raison de ces différences, et parce que les API Windows ne sont pas des objets COM, l’interopérabilité avec les API Windows et le .NET Framework est effectuée à l’aide de l’appel de code non managé ou de PInvoke. L’appel de code non managé est un service qui permet au code managé d’appeler des fonctions non managées implémentées dans des dll. Pour plus d’informations, consultez [consommation de fonctions DLL non managées](../../../framework/interop/consuming-unmanaged-dll-functions.md). Vous pouvez utiliser PInvoke dans Visual Basic à l’aide de l' `Declare` instruction ou en appliquant l' `DllImport` attribut à une procédure vide.  
  
 Les appels d’API Windows étaient un élément important de la programmation de Visual Basic, mais ils sont rarement nécessaires avec Visual Basic .NET. Dans la mesure du possible, vous devez utiliser du code managé à partir de la .NET Framework pour effectuer des tâches, et non des appels d’API Windows. Cette procédure pas à pas fournit des informations pour les situations dans lesquelles l’utilisation des API Windows est nécessaire.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Appels d’API à l’aide de DECLARE  

 La méthode la plus courante pour appeler des API Windows consiste à utiliser l' `Declare` instruction.  
  
### <a name="to-declare-a-dll-procedure"></a>Pour déclarer une procédure DLL  
  
1. Déterminez le nom de la fonction que vous souhaitez appeler, plus ses arguments, types d’arguments et valeur de retour, ainsi que le nom et l’emplacement de la DLL qui la contient.  
  
    > [!NOTE]
    > Pour obtenir des informations complètes sur les API Windows, consultez la documentation du kit de développement logiciel (SDK) Win32 dans l’API Windows du kit de développement Platform SDK. Pour plus d’informations sur les constantes utilisées par les API Windows, examinez les fichiers d’en-tête, tels que Windows. h, inclus dans le kit de développement Platform SDK.  
  
2. Ouvrez un nouveau projet d’application Windows en cliquant sur **nouveau** dans le menu **fichier** , puis sur **projet**. La boîte de dialogue **Nouveau projet** apparaît.  
  
3. Sélectionnez **application Windows** dans la liste des modèles de projet de Visual Basic. Le nouveau projet s’affiche.  
  
4. Ajoutez la `Declare` fonction suivante à la classe ou au module dans lequel vous souhaitez utiliser la dll :  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Parties de l’instruction DECLARE  

 L' `Declare` instruction comprend les éléments suivants.  
  
#### <a name="auto-modifier"></a>Modificateur automatique  

 Le `Auto` modificateur indique au runtime de convertir la chaîne en fonction du nom de la méthode en fonction des règles de Common Language Runtime (ou du nom d’alias, si elle est spécifiée).  
  
#### <a name="lib-and-alias-keywords"></a>Mots clés lib et alias  

 Le nom qui suit le `Function` mot clé est le nom que votre programme utilise pour accéder à la fonction importée. Il peut être identique au nom réel de la fonction que vous appelez, ou vous pouvez utiliser n’importe quel nom de procédure valide, puis utiliser le `Alias` mot clé pour spécifier le nom réel de la fonction que vous appelez.  
  
 Spécifiez le `Lib` mot clé, suivi du nom et de l’emplacement de la dll qui contient la fonction que vous appelez. Vous n’avez pas besoin de spécifier le chemin d’accès pour les fichiers situés dans les répertoires système Windows.  
  
 Utilisez le `Alias` mot clé si le nom de la fonction que vous appelez n’est pas un nom de procédure Visual Basic valide, ou est en conflit avec le nom d’autres éléments dans votre application. `Alias` indique le nom réel de la fonction appelée.  
  
#### <a name="argument-and-data-type-declarations"></a>Déclarations de type d’argument et de données  

 Déclarez les arguments et leurs types de données. Cette partie peut être complexe, car les types de données utilisés par Windows ne correspondent pas aux types de données Visual Studio. Visual Basic effectue un grand nombre de tâches pour vous en convertissant les arguments en types de données compatibles, un processus appelé *marshaling*. Vous pouvez contrôler explicitement la manière dont les arguments sont marshalés à l’aide de l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut défini dans l' <xref:System.Runtime.InteropServices> espace de noms.  
  
> [!NOTE]
> Les versions précédentes de Visual Basic vous permettaient de déclarer des paramètres `As Any` , ce qui signifie que les données de n’importe quel type de données pouvaient être utilisées. Visual Basic requiert l’utilisation d’un type de données spécifique pour toutes les `Declare` instructions.  
  
#### <a name="windows-api-constants"></a>Constantes de l’API Windows  

 Certains arguments sont des combinaisons de constantes. Par exemple, l' `MessageBox` API illustrée dans cette procédure pas à pas accepte un argument entier appelé `Typ` qui contrôle le mode d’affichage de la boîte de message. Vous pouvez déterminer la valeur numérique de ces constantes en examinant les `#define` instructions dans le fichier winuser. h. Les valeurs numériques sont généralement affichées au format hexadécimal. vous pouvez donc utiliser une calculatrice pour les ajouter et les convertir au format décimal. Par exemple, si vous souhaitez combiner les constantes pour le style d’exclamation `MB_ICONEXCLAMATION` 0x00000030 et le style Yes/No `MB_YESNO` 0x00000004, vous pouvez ajouter les nombres et obtenir le résultat 0x00000034, ou 52 décimal. Bien que vous puissiez utiliser le résultat décimal directement, il est préférable de déclarer ces valeurs en tant que constantes dans votre application et de les combiner à l’aide de l' `Or` opérateur.  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>Pour déclarer des constantes pour les appels d’API Windows  
  
1. Consultez la documentation de la fonction Windows que vous appelez. Déterminez le nom des constantes qu’il utilise et le nom du fichier. h qui contient les valeurs numériques de ces constantes.  
  
2. Utilisez un éditeur de texte, tel que le bloc-notes, pour afficher le contenu du fichier d’en-tête (. h) et rechercher les valeurs associées aux constantes que vous utilisez. Par exemple, l' `MessageBox` API utilise la constante `MB_ICONQUESTION` pour afficher un point d’interrogation dans la boîte de message. La définition de `MB_ICONQUESTION` est dans winuser. h et se présente comme suit :  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Ajoutez `Const` des instructions équivalentes à votre classe ou module pour rendre ces constantes disponibles pour votre application. Par exemple :  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>Pour appeler la procédure DLL  
  
1. Ajoutez un bouton nommé `Button1` au formulaire de démarrage de votre projet, puis double-cliquez dessus pour afficher son code. Le gestionnaire d’événements du bouton s’affiche.  
  
2. Ajoutez du code au `Click` Gestionnaire d’événements pour le bouton que vous avez ajouté, pour appeler la procédure et fournir les arguments appropriés :  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. Exécutez le projet en appuyant sur F5. La boîte de message s’affiche avec les boutons de réponse **Oui** et **non** . Cliquez sur l’un des deux.  
  
#### <a name="data-marshaling"></a>Marshaling de données  

 Visual Basic convertit automatiquement les types de données des paramètres et des valeurs de retour pour les appels d’API Windows, mais vous pouvez utiliser l' `MarshalAs` attribut pour spécifier explicitement les types de données non managés attendus par une API. Pour plus d’informations sur le marshaling d’interopérabilité, consultez [marshaling d’interopérabilité](../../../framework/interop/interop-marshaling.md).  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Pour utiliser DECLARE et MarshalAs dans un appel d’API  
  
1. Déterminez le nom de la fonction que vous souhaitez appeler, ainsi que ses arguments, les types de données et la valeur de retour.  
  
2. Pour simplifier l’accès à l' `MarshalAs` attribut, ajoutez une `Imports` instruction en haut du code pour la classe ou le module, comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. Ajoutez un prototype de fonction pour la fonction importée à la classe ou au module que vous utilisez, puis appliquez l' `MarshalAs` attribut aux paramètres ou à la valeur de retour. Dans l’exemple suivant, un appel d’API qui attend le type `void*` est marshalé en tant que `AsAny` :  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Appels d’API à l’aide de DllImport  

 L' `DllImport` attribut fournit une deuxième méthode pour appeler des fonctions dans des dll sans bibliothèques de types. `DllImport` est à peu près équivalent à l’utilisation d’une `Declare` instruction, mais offre davantage de contrôle sur la façon dont les fonctions sont appelées.  
  
 Vous pouvez utiliser `DllImport` avec la plupart des appels d’API Windows tant que l’appel fait référence à une méthode partagée (parfois appelée *statique*). Vous ne pouvez pas utiliser de méthodes qui requièrent une instance d’une classe. Contrairement aux `Declare` instructions, `DllImport` les appels ne peuvent pas utiliser l' `MarshalAs` attribut.  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Pour appeler une API Windows à l’aide de l’attribut DllImport  
  
1. Ouvrez un nouveau projet d’application Windows en cliquant sur **nouveau** dans le menu **fichier** , puis sur **projet**. La boîte de dialogue **Nouveau projet** apparaît.  
  
2. Sélectionnez **application Windows** dans la liste des modèles de projet de Visual Basic. Le nouveau projet s’affiche.  
  
3. Ajoutez un bouton nommé `Button2` au formulaire de démarrage.  
  
4. Double-cliquez `Button2` pour ouvrir le mode Code du formulaire.  
  
5. Pour simplifier l’accès à `DllImport` , ajoutez une `Imports` instruction en haut du code pour la classe Startup Form :  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Déclarez une fonction vide avant l' `End Class` instruction pour le formulaire et nommez la fonction `MoveFile` .  
  
7. Appliquez les `Public` `Shared` modificateurs et à la déclaration de fonction et définissez les paramètres pour `MoveFile` en fonction des arguments que la fonction API Windows utilise :  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Votre fonction peut avoir n’importe quel nom de procédure valide ; l' `DllImport` attribut spécifie le nom dans la dll. Il gère également le marshaling d’interopérabilité pour les paramètres et les valeurs de retour. vous pouvez donc choisir des types de données Visual Studio similaires aux types de données utilisés par l’API.  
  
8. Appliquez l' `DllImport` attribut à la fonction vide. Le premier paramètre est le nom et l’emplacement de la DLL contenant la fonction que vous appelez. Vous n’avez pas besoin de spécifier le chemin d’accès pour les fichiers situés dans les répertoires système Windows. Le deuxième paramètre est un argument nommé qui spécifie le nom de la fonction dans l’API Windows. Dans cet exemple, l' `DllImport` attribut force les appels à à `MoveFile` être transmis à `MoveFileW` dans KERNEL32.DLL. La `MoveFileW` méthode copie un fichier à partir du chemin d’accès `src` vers le chemin d’accès `dst` .  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Ajoutez du code au `Button2_Click` Gestionnaire d’événements pour appeler la fonction :  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Créez un fichier nommé Test.txt et placez-le dans le répertoire C:\Tmp sur votre disque dur. Créez le répertoire tmp si nécessaire.  
  
11. Appuyez sur F5 pour démarrer l'application. Le formulaire principal s’affiche.  
  
12. Cliquez sur **button2**. Le message « le fichier a été déplacé avec succès » s’affiche si le fichier peut être déplacé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare Statement](../../language-reference/statements/declare-statement.md)
- [Automatique](../../language-reference/modifiers/auto.md)
- [Alias](../../language-reference/statements/alias-clause.md)
- [COM Interop](index.md)
- [Création de prototypes dans du code managé](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Marshaling d'un délégué comme méthode de rappel](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
