---
title: -appconfig (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922521"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (Options du compilateur C#)
L’option du compilateur **-appconfig** permet à une application C# d’indiquer l’emplacement du fichier de configuration de l’application (app.config) d’un assembly au CLR (Common Language Runtime) au moment de la liaison de l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Obligatoire. Fichier de configuration de l’application qui contient des paramètres de liaison de l’assembly.  
  
## <a name="remarks"></a>Notes   
 **-appconfig** est notamment utilisé dans des scénarios avancés dans lesquels un assembly doit simultanément référencer à la fois la version du .NET Framework et la version du .NET Framework pour Silverlight d’un assembly de référence particulier. Par exemple, un concepteur XAML écrit dans WPF (Windows Presentation Foundation) devra peut-être référencer à la fois le bureau WPF pour l’interface utilisateur du concepteur et le sous-ensemble de WPF qui est fourni avec Silverlight. Le même assembly de concepteur doit accéder aux deux assemblys. Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents.  
  
 L’option du compilateur **-appconfig** vous permet de spécifier l’emplacement d’un fichier app.config qui désactive le comportement par défaut à l’aide d’une balise `<supportPortability>`, comme indiqué dans l’exemple suivant.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Le compilateur passe l’emplacement du fichier à la logique de liaison d’assembly du CLR.  
  
> [!NOTE]
> Si vous utilisez MSBuild (Microsoft Build Engine) pour générer votre application, vous pouvez définir l’option du compilateur **-appconfig** en ajoutant une balise de propriété au fichier .csproj. Pour utiliser le fichier app.config qui est déjà défini dans le projet, ajoutez la balise de propriété `<UseAppConfigForCompiler>` au fichier .csproj et affectez-lui la valeur `true`. Pour spécifier un autre fichier app.config, ajoutez la balise de propriété `<AppConfigForCompiler>` et définissez sa valeur sur l’emplacement du fichier.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant affiche un fichier app.config qui permet à une application d’avoir des références à la fois à l’implémentation .NET Framework et à l’implémentation .NET Framework pour Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations. L’option du compilateur **-appconfig** spécifie l’emplacement de ce fichier app.config.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [\<supportPortability> Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Options du compilateur C# par ordre alphabétique](./listed-alphabetically.md)
