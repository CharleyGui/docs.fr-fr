---
title: 'Comment : créer et initialiser les sources de trace'
description: Créez et initialisez les sources de trace à l’aide de la classe TraceSource dans .NET. Cette classe fournit des méthodes pour le suivi des événements et des données et l’émission de traces d’informations.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
ms.openlocfilehash: 55d7854bff991ba185d3f5d6e4c6e7222c9e3039
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051270"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Comment : créer et initialiser les sources de trace
La classe <xref:System.Diagnostics.TraceSource> est utilisée par les applications pour produire des traces qui peuvent être associées à l'application. <xref:System.Diagnostics.TraceSource> fournit des méthodes de traçage qui vous permettent de tracer facilement des événements et des données, ainsi que de fournir des traces d'information. Il est possible de créer et d'initialiser une sortie de trace <xref:System.Diagnostics.TraceSource> en utilisant ou non les fichiers de configuration. Cette rubrique fournit des instructions pour les deux options. Toutefois, nous vous recommandons d'utiliser des fichiers de configuration pour simplifier la reconfiguration des traces produites par les sources de trace au moment de l'exécution.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Pour créer et initialiser une source de trace à l'aide d'un fichier de configuration  
  
1. Créez un projet d’application console Visual Studio (.NET Framework) et remplacez le code fourni par le code suivant. Ce code consigne les erreurs et les avertissements et renvoie certains d'entre eux vers la console et d'autres vers le fichier myListener créé par les entrées dans le fichier de configuration.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Ajoutez un fichier de configuration d'application, s'il n'en existe pas encore, au projet pour initialiser la source de trace nommée `TraceSourceApp` dans l'exemple de code à l'étape 1.  
  
3. Remplacez le contenu du fichier de configuration par défaut par les paramètres suivants pour initialiser un écouteur de suivi de console et un écouteur de suivi de TextWriter pour la source de trace créée à l'étape 1.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"
            switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"
            type="System.Diagnostics.TextWriterTraceListener"
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     En plus de configurer les écouteurs de la trace, le fichier de configuration crée des filtres pour les deux écouteurs et un commutateur de source pour la source de trace. L'exemple illustre deux techniques pour ajouter des écouteurs de la trace : l'ajout direct de l'écouteur à la source de trace et l'ajout d'un écouteur à la collection d'écouteurs partagés suivi de l'ajout de son nom à la source de trace. Les filtres identifiés pour les deux écouteurs sont initialisés avec des niveaux de source différents. Par conséquent, certains messages ne sont écrits que par un seul des deux écouteurs.  
  
     Le fichier de configuration initialise les paramètres de la source de trace lors de l'initialisation de l'application. L'application peut modifier dynamiquement les propriétés définies par le fichier de configuration pour substituer des paramètres spécifiés par l'utilisateur. Vous pouvez, par exemple, décider que les messages critiques seront toujours envoyés vers un fichier texte, quels que soient les paramètres de configuration actuelle. L'exemple de code montre comment remplacer des paramètres du fichier de configuration pour garantir que les messages critiques sont envoyés aux écouteurs de suivi.  
  
     La modification des paramètres du fichier de configuration lorsque l'application est en cours d'exécution ne change pas les paramètres d'origine. Pour modifier les paramètres, vous devez redémarrer l'application ou l'actualiser par programmation à l'aide de la méthode <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Pour initialiser des sources de trace, des écouteurs et des filtres sans fichier de configuration  
  
- Utilisez le code d'exemple suivant pour activer le traçage par une source de trace sans utiliser un fichier de configuration. Il ne s'agit pas d'une pratique recommandée, mais il peut arriver que vous ne souhaitiez pas dépendre des fichiers de configuration pour assurer le traçage.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Traçage et instrumentation d'applications](tracing-and-instrumenting-applications.md)
