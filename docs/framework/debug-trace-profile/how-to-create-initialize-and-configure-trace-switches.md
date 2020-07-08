---
title: 'Comment : créer, initialiser et configurer les commutateurs de traçage'
description: Créez, initialisez et configurez les commutateurs de trace à l’aide des classes System. Diagnostics. BooleanSwitch et System. Diagnostics. TraceSwitch dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 6a43e143abba96c841f04b7be9d482c55e78aa8f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051322"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Comment : créer, initialiser et configurer les commutateurs de traçage
Les commutateurs de trace vous permettent d'activer ou de désactiver la sortie de traçage, et de la filtrer.  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a>Création et initialisation d’un commutateur de suivi  
 Pour pouvoir utiliser des commutateurs de trace, vous devez tout d'abord les créer et les placer dans votre code. Il existe deux classes prédéfinies à partir desquelles vous pouvez créer des objets commutateur : la classe <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> et la classe <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>. Utilisez <xref:System.Diagnostics.BooleanSwitch> si vous souhaitez uniquement contrôler l'affichage des messages de trace. Utilisez <xref:System.Diagnostics.TraceSwitch> si vous avez besoin de faire la distinction entre plusieurs niveaux de trace. Si vous utilisez un commutateur <xref:System.Diagnostics.TraceSwitch>, vous pouvez définir vos propres messages de débogage et les associer à différents niveaux de trace. Vous pouvez utiliser les deux types de commutateurs pour le traçage ou le débogage. Par défaut, <xref:System.Diagnostics.BooleanSwitch> est désactivé et <xref:System.Diagnostics.TraceSwitch> est associé au niveau <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Vous pouvez placer les commutateurs de trace que vous créez dans toute partie de votre code susceptible de les utiliser.  
  
 Vous avez la possibilité de définir les niveaux de trace et d'autres options de configuration directement dans le code, mais il est recommandé d'utiliser le fichier de configuration pour gérer l'état de vos commutateurs. La gestion de la configuration de vos commutateurs dans le système de configuration vous donne en effet plus de souplesse : vous pouvez activer ou désactiver plusieurs commutateurs et changer de niveau sans avoir à recompiler votre application.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Pour créer et initialiser un commutateur de trace  
  
1. Définissez un commutateur de type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> ou de type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, puis indiquez le nom et la description du commutateur.  
  
2. Configurez votre commutateur de trace. Pour plus d’informations, consultez [Configuration des commutateurs de suivi](#configure).  
  
     Le code suivant crée deux commutateurs, un de chaque type :  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =
       new System.Diagnostics.TraceSwitch("General",
       "Entire application");  
    ```  
  
<a name="configure"></a>
## <a name="configuring-trace-switches"></a>Configuration des commutateurs de suivi  
 Après avoir distribué votre application, vous gardez la possibilité d'activer ou de désactiver la sortie de trace en configurant les commutateurs de trace dans votre application. Pour configurer un commutateur, il faut modifier sa valeur à partir d'une source externe une fois qu'il a été initialisé. Vous pouvez modifier les valeurs des objets commutateur à l'aide du fichier de configuration. Vous configurez un commutateur de trace pour pouvoir l'activer et le désactiver ou pour définir le niveau de trace associé, qui détermine la quantité et le type de messages qu'il transmet aux écouteurs.  
  
 Vos commutateurs sont configurés à l'aide du fichier .config. Pour une application web, il s'agit du fichier Web.config associé au projet. Dans une application Windows, ce fichier est nommé (nom de l’application) .exe.config. Dans une application déployée, ce fichier doit résider dans le même dossier que l’exécutable.  
  
 Quand votre application exécute le code qui crée pour la première fois une instance d'un commutateur, elle recherche dans le fichier de configuration des informations sur le niveau de trace défini pour le commutateur indiqué. Le système de traçage examine le fichier de configuration une seule fois pour un commutateur donné (la première fois que votre application crée le commutateur).  
  
 Dans une application déployée, vous activez le code de trace en reconfigurant les objets commutateur quand votre application n'est pas en cours d'exécution. Généralement, cela implique l'activation et la désactivation des objets commutateur ou le changement des niveaux de trace, puis le redémarrage de votre application.  
  
 Quand vous créez une instance d’un commutateur, vous l’initialisez également en spécifiant deux arguments : l’argument *displayName* et l’argument *description*. L’argument *displayName* du constructeur définit la propriété <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> de l’instance de classe <xref:System.Diagnostics.Switch>. L’argument *displayName* correspond au nom utilisé pour configurer le commutateur dans le fichier .config. L’argument *description* doit normalement retourner une brève description du commutateur, ainsi que les messages qu’il contrôle.  
  
 En plus de spécifier le nom du commutateur que vous configurez, vous devez lui attribuer une valeur. Cette valeur est un nombre entier. Pour <xref:System.Diagnostics.BooleanSwitch>, la valeur zéro (0) correspond à **Off** (Désactivé), et toute autre valeur correspond à **On** (Activé). Pour <xref:System.Diagnostics.TraceSwitch>, les valeurs 0, 1, 2, 3 et 4 correspondent respectivement à **Off** (Désactivé), **Error** (Erreur), **Warning** (Avertissement), **Info** (Information) et **Verbose** (Commentaires). Toute valeur supérieure à 4 est traitée comme **Verbose**, et toute valeur inférieure à 0 est traitée comme **Off**.  
  
> [!NOTE]
> Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte. Par exemple, `true` pour un commutateur <xref:System.Diagnostics.BooleanSwitch> ou le texte représentant une valeur d'énumération comme `Error` pour un commutateur <xref:System.Diagnostics.TraceSwitch>. La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.  
  
 Pour que les utilisateurs finals puissent configurer les commutateurs de trace d'une application, vous devez fournir des informations détaillées sur les commutateurs dans votre application. Décrivez en détail ce que les commutateurs contrôlent et comment ils peuvent être activés ou désactivés. Transmettez également aux utilisateurs finals un fichier .config contenant l'aide nécessaire dans les commentaires.  
  
#### <a name="to-configure-trace-switches"></a>Pour configurer les commutateurs de trace  
  
1. Pour utiliser les commutateurs de suivi, vous devez d’abord les créer et les placer dans votre code, comme décrit dans la section [Création et initialisation d’un commutateur de suivi](#create).  
  
2. Si votre projet ne contient pas de fichier de configuration (app.config ou Web.config), dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.  
  
    - **Visual Basic** : dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier de configuration de l’application**.  
  
         Le fichier de configuration de l'application est créé, puis ouvert. Il s'agit d'un document XML dont l'élément racine est `<configuration>.`  
  
    - **Visual C#**  : dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier XML**. Nommez ce fichier **app.config**. Dans l’éditeur XML, après la déclaration XML, ajoutez le code XML suivant :  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Au moment de la compilation de votre projet, le fichier app.config est copié dans le dossier de sortie du projet et renommé *nom_application*.exe.config.  
  
3. Entre la balise `<configuration>` et la balise `</configuration>`, ajoutez le code XML approprié pour configurer vos commutateurs. Les exemples suivants montrent un commutateur **BooleanSwitch** dont la propriété **DisplayName** a la valeur `DataMessageSwitch` et un commutateur **TraceSwitch** dont la propriété **DisplayName** a la valeur `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     Dans cette configuration, les deux commutateurs sont désactivés.  
  
4. Si vous avez besoin d’activer un commutateur **BooleanSwitch**, tel que le commutateur `DataMessagesSwitch` montré dans l’exemple précédent, remplacez **Value** par un nombre entier différent de zéro (0).  
  
5. Si vous avez besoin d’activer un commutateur **TraceSwitch**, tel que le commutateur `TraceLevelSwitch` montré dans l’exemple précédent, remplacez **Value** par le paramètre correspondant au niveau approprié (1 à 4).  
  
6. Ajoutez des commentaires dans le fichier .config pour expliquer clairement à l'utilisateur quelles valeurs il doit modifier pour configurer les commutateurs de manière appropriée.  
  
     L'exemple suivant montre à quoi le code final, commentaires inclus, peut ressembler :  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Traçage et instrumentation d'applications](tracing-and-instrumenting-applications.md)
- [Comment : ajouter des instructions de traçage dans le code d'une application](how-to-add-trace-statements-to-application-code.md)
- [Commutateurs de traçage](trace-switches.md)
- [Schéma des paramètres de traçage et de débogage](../configure-apps/file-schema/trace-debug/index.md)
