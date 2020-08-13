---
title: Classe ControlBuilderInterceptor
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 0cd7409deb9cb84783cfa70600999fa4b2a2d2e2
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187988"
---
# <a name="controlbuilderinterceptor-class"></a>Classe ControlBuilderInterceptor

La `ControlBuilderInterceptor` classe permet de personnaliser ou de contrôler le processus de compilation.

## <a name="syntax"></a>Syntaxe

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> La `ControlBuilderInterceptor` classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Comme décrit dans la section Notes, l’existence de ce type peut être vérifiée pour déterminer si la prise en charge du type d’intercepteur est présente. Microsoft ne prend en charge aucune autre utilisation de cette classe dans une application de production, dans toutes les circonstances.

## <a name="remarks"></a>Notes

Dans .NET Framework 2,0 et .NET Framework 3,5, les mises à jour d' [août 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) ajoutent la prise en charge de l’utilisation d’un type d’intercepteur pour personnaliser ou contrôler le processus de compilation. Vous pouvez déterminer si cette prise en charge est présente en utilisant <xref:System.Type.GetType?displayProperty=nameWithType> pour vérifier l’existence du `ControlBuilderInterceptor` type, comme illustré dans le code suivant.

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

Si la valeur de retour n’est pas null, la prise en charge de l’intercepteur est présente. Si la valeur de retour est `null` , ou si une exception est levée, les mises à jour du 2020 d’août n’ont pas été installées et la prise en charge de l’intercepteur est absente.

Si la prise en charge de l’intercepteur est présente, vous pouvez écrire et inscrire un type d’intercepteur qui interagit avec le processus de compilation exactement de la même façon que <xref:System.Web.Compilation.ControlBuilderInterceptor> dans les versions ultérieures de .NET Framework. Dans .NET Framework 2,0 et .NET Framework 3,5, le type d’intercepteur peut être n’importe quelle classe qui répond aux exigences suivantes :

* A un constructeur sans paramètre public.
* A des méthodes publiques et non statiques nommées `PreControlBuilderInit` et ayant `OnProcessGeneratedCode` la même signature et la même sémantique que les <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> méthodes et, qui existent dans les versions ultérieures de .NET Framework.

Inscrivez le type d’intercepteur à l’aide `aspnet:20ControlBuilderInterceptor` de la clé dans les paramètres d’application ASP.net ( `<appSettings>` ). Ce paramètre d’application doit être indiqué dans le fichier de *web.config* de votre ordinateur ou de votre application. Spécifiez le type d’intercepteur à l’aide de son nom de type qualifié d’assembly. L’exemple suivant montre comment inscrire un type d’intercepteur nommé `Fabrikam.Interceptor` .

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

Pour récupérer le nom qualifié d’assembly d’un type, utilisez la <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> propriété, comme illustré dans le code suivant.

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

Lorsque la prise en charge de l’intercepteur est présente, le processus de compilation interagit avec le type répertorié de la manière décrite ci-dessus. Lorsque la prise en charge de l’intercepteur est absente, le paramètre d’application est ignoré et n’a aucun effet.

## <a name="requirements"></a>Configuration requise

**Espace de noms :** System. Web. Compilation

**Assembly :** System. Web (en System.Web.dll)

**Versions de .NET Framework :** 3,5, 2,0
