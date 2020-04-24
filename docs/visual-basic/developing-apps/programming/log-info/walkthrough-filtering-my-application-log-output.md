---
title: filtrage de la sortie de My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353588"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Procédure pas à pas : filtrage de la sortie de My.Application.Log (Visual Basic)

Cette procédure pas à pas montre comment modifier le filtrage de journal par défaut de l’objet `My.Application.Log` pour contrôler les informations passées de l’objet `Log` aux écouteurs et celles qui sont écrites par les écouteurs. Vous pouvez modifier le comportement de journalisation même après avoir généré l’application, car les informations de configuration sont stockées dans le fichier de configuration de l’application.

## <a name="getting-started"></a>Mise en route

Chaque message écrit par `My.Application.Log` a un niveau de gravité associé que les mécanismes de filtrage utilisent pour contrôler la sortie de journal. Cet exemple d’application utilise les méthodes `My.Application.Log` pour écrire plusieurs messages de journal avec différents niveaux de gravité.

#### <a name="to-build-the-sample-application"></a>Pour générer l’exemple d’application

1. Ouvrez un nouveau projet d’application Windows Visual Basic.

2. Ajoutez un bouton nommé Button1 à Form1.

3. Dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> de Button1, ajoutez le code suivant :

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Exécutez l’application dans le débogueur.

5. Appuyez sur **Button1**.

     L’application écrit les informations suivantes dans le fichier journal et la sortie de débogage de l’application.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Fermez l'application.

     Pour plus d’informations sur la consultation de la fenêtre de sortie de débogage de l’application, consultez [Fenêtre Sortie](/visualstudio/ide/reference/output-window). Pour plus d’informations sur l’emplacement du fichier journal de l’application, consultez [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Par défaut, l’application vide la sortie du fichier journal quand elle se ferme.

     Dans l’exemple ci-dessus, le deuxième appel à la méthode <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> et l’appel à la méthode <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> génèrent la sortie de journal, ce qui n’est pas le cas des premier et dernier appels à la méthode `WriteEntry`. Étant donné que les niveaux de gravité de `WriteEntry` et `WriteException` sont « Information » et « Erreur », ceux-ci sont autorisés par le filtrage de journal par défaut de l’objet `My.Application.Log`. Toutefois, les événements avec les niveaux de gravité « Démarrage » et « Arrêt » ne peuvent pas générer une sortie de journal.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrage de tous les écouteurs My.Application.Log

L’objet `My.Application.Log` utilise un <xref:System.Diagnostics.SourceSwitch> nommé `DefaultSwitch` pour gérer les messages qu’il passe des méthodes `WriteEntry` et `WriteException` aux écouteurs de journalisation. Vous pouvez configurer `DefaultSwitch` dans le fichier de configuration de l’application en lui affectant l’une des valeurs d’énumération <xref:System.Diagnostics.SourceLevels>. Par défaut, sa valeur est « Information ».

Ce tableau affiche le niveau de gravité requis pour le journal afin d’écrire un message pour les écouteurs, avec un paramètre `DefaultSwitch` particulier.

|Valeur DefaultSwitch|Gravité du message nécessaire pour la sortie|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` ou `Error`|
|`Warning`|`Critical`, `Error` ou `Warning`|
|`Information`|`Critical`, `Error`, `Warning` ou `Information`|
|`Verbose`|`Critical`, `Error`, `Warning`, `Information` ou`Verbose`|
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume` ou`Transfer`|
|`All`|Tous les messages sont autorisés.|
|`Off`|Tous les messages sont bloqués.|

> [!NOTE]
> Les méthodes `WriteEntry` et `WriteException` ont chacune une surcharge qui ne spécifie pas de niveau de gravité. Le niveau de gravité implicite de la surcharge `WriteEntry` est « Information » et le niveau de gravité implicite de la surcharge `WriteException` est « Erreur ».

Ce tableau explique la sortie de journal affichée dans l’exemple précédent : avec la valeur « Information » du paramètre `DefaultSwitch` par défaut, seuls le deuxième appel à la méthode `WriteEntry` et l’appel à la méthode `WriteException` génèrent la sortie de journal.

#### <a name="to-log-only-activity-tracing-events"></a>Pour enregistrer uniquement les événements de traçage d’activités

1. Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et sélectionnez **Ouvrir**.

     -ou-

     S’il n’existe pas de fichier app.config :

    1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

    2. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.

    3. Cliquez sur **Ajouter**.

2. Recherchez la section `<switches>` dans la section `<system.diagnostics>`, qui se trouve dans la section `<configuration>` de niveau supérieur.

3. Recherchez l’élément qui ajoute `DefaultSwitch` à la collection de commutateurs. Il doit ressembler à l’élément ci-après :

     `<add name="DefaultSwitch" value="Information" />`

4. Remplacez la valeur de l’attribut `value` par « ActivityTracing ».

5. Le contenu du fichier app.config doit être similaire au code XML suivant :

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. Exécutez l’application dans le débogueur.

7. Appuyez sur **Button1**.

     L’application écrit les informations suivantes dans le fichier journal et la sortie de débogage de l’application :

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Fermez l'application.

9. Rétablissez la valeur « Information » de l’attribut `value`.

    > [!NOTE]
    > Le paramètre de commutateur `DefaultSwitch` contrôle uniquement `My.Application.Log`. Il ne modifie pas le comportement des classes <xref:System.Diagnostics.Trace?displayProperty=nameWithType> et <xref:System.Diagnostics.Debug?displayProperty=nameWithType> .NET Framework.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Filtrage individuel des écouteurs My.Application.Log

L’exemple précédent indique comment modifier le filtrage de toute la sortie `My.Application.Log`. Cet exemple montre comment filtrer un écouteur de journalisation. Par défaut, une application a deux écouteurs qui écrivent dans le fichier journal et la sortie de débogage de l’application.

Le fichier de configuration contrôle le comportement des écouteurs de journalisation en permettant à chacun d’eux d’avoir un filtre similaire à un commutateur pour `My.Application.Log`. Un écouteur de journalisation ne génère un message que si la gravité de ce dernier est acceptée par le `DefaultSwitch` du journal et le filtre de l’écouteur de journalisation.

Cet exemple montre comment configurer le filtrage d’un nouvel écouteur de débogage et l’ajouter à l’objet `Log`. L’écouteur de débogage par défaut doit être supprimé de l’objet `Log` ; ainsi, il apparaît clairement que les messages de débogage proviennent du nouvel écouteur de débogage.

#### <a name="to-log-only-activity-tracing-events"></a>Pour enregistrer uniquement les événements de traçage d’activités

1. Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et sélectionnez **Ouvrir**.

     \- ou -

     S’il n’existe pas de fichier app.config :

    1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

    2. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.

    3. Cliquez sur **Ajouter**.

2. Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions**. Choisissez **Ouvrir**.

3. Recherchez la section `<listeners>`, dans la section `<source>` avec l’attribut `name` « DefaultSource » sous la section `<sources>`. La section `<sources>` est sous la section `<system.diagnostics>`, dans la section `<configuration>` de niveau supérieur.

4. Ajoutez cet élément à la section `<listeners>` :

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.

6. Ajoutez cet élément à cette section `<sharedListeners>` :

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     Le filtre <xref:System.Diagnostics.EventTypeFilter> considère l’une des valeurs d’énumération <xref:System.Diagnostics.SourceLevels> comme son attribut `initializeData`.

7. Le contenu du fichier app.config doit être similaire au code XML suivant :

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. Exécutez l’application dans le débogueur.

9. Appuyez sur **Button1**.

     L’application écrit les informations suivantes dans le fichier journal de l’application :

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     L’application écrit moins d’informations dans la sortie de débogage de l’application à cause du filtrage plus restrictif.

     `Default Error   2   Error`

10. Fermez l'application.

Pour plus d’informations sur la modification des paramètres de journal après le déploiement, consultez [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Procédure pas à pas : création d’écouteurs de journalisation personnalisés](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Procédure : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Commutateurs de traçage](../../../../framework/debug-trace-profile/trace-switches.md)
- [Enregistrement d’informations provenant de l’application](../../../../visual-basic/developing-apps/programming/log-info/index.md)
