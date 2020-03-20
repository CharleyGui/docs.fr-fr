---
title: Exécution côte à côte in-process
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 5ca2f03576946a23b3133bbe7532d46c4ad758ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181662"
---
# <a name="in-process-side-by-side-execution"></a>Exécution côte à côte in-process
À compter de .NET Framework 4, vous pouvez utiliser l’hébergement côte à côte in-process pour exécuter plusieurs versions du CLR (Common Language Runtime) dans un processus unique. Par défaut, les composants COM managés s’exécutent avec la version du .NET Framework avec laquelle ils ont été générés, indépendamment de la version du .NET Framework chargée pour le processus.  
  
## <a name="background"></a>Arrière-plan  
 Le .NET Framework a toujours fourni un hébergement côte à côte pour les applications de code managé, mais avant .NET Framework 4, il ne fournissait pas cette fonctionnalité pour les composants COM managés. Dans le passé, les composants COM managés chargés dans un processus étaient exécutés avec la version du runtime déjà chargée ou avec la version installée la plus récente du .NET Framework. Si cette version n’était pas compatible avec le composant COM, le composant échouait.  
  
 .NET Framework 4 fournit une nouvelle approche de l’hébergement côte à côte qui s’assure des éléments suivants :  
  
- L’installation d’une nouvelle version du .NET Framework n’a aucun effet sur les applications existantes.  
  
- Les applications sont exécutées avec la version du .NET Framework avec laquelle elles ont été générées. Elles n’utilisent pas la nouvelle version du .NET Framework, à moins que cela ne leur soit expressément demandé. Il est toutefois plus facile pour les applications de passer à une nouvelle version du .NET Framework.  
  
## <a name="effects-on-users-and-developers"></a>Effets sur les utilisateurs et les développeurs  
  
- **Utilisateurs finaux et administrateurs système**. Ces utilisateurs savent désormais que, quand ils installent une nouvelle version du runtime, soit indépendamment soit avec une application, cela n’aura aucun impact sur leurs ordinateurs. Les applications existantes continueront de fonctionner comme auparavant.  
  
- **Développeurs d’applications**. L’hébergement côte à côte n’a presque aucun effet sur les développeurs d’applications. Par défaut, les applications sont toujours exécutées avec la version du .NET Framework avec laquelle elles ont été créées. Cela n’a pas changé. Toutefois, les développeurs peuvent substituer ce comportement et demander à l’application de s’exécuter sous une version plus récente du .NET Framework (consultez le [scénario 2](#scenarios)).  
  
- **Consommateurs et développeurs de bibliothèques**. L’hébergement côte à côte ne résout pas les problèmes de compatibilité rencontrés par les développeurs de bibliothèques. Une bibliothèque chargée directement par une application, soit via une référence directe soit via un appel <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, continue d’utiliser le runtime du <xref:System.AppDomain> dans lequel elle est chargée. Vous devez tester vos bibliothèques sur toutes les versions du .NET Framework que vous souhaitez prendre en charge. Si une application est compilée à l’aide du runtime .NET Framework 4 mais inclut une bibliothèque créée à l’aide d’un runtime antérieur, cette bibliothèque utilisera également le runtime .NET Framework 4. Toutefois, si vous possédez une application générée à l’aide d’un runtime antérieur et une bibliothèque créée à l’aide de .NET Framework 4, vous devez forcer votre application à utiliser également .NET Framework 4 (consultez le [scénario 3](#scenarios)).  
  
- **Développeurs de composants COM managés**. Dans le passé, les composants COM managés étaient automatiquement exécutés à l’aide de la version la plus récente du runtime installée sur l’ordinateur. Vous pouvez maintenant exécuter les composants COM avec la version du runtime avec laquelle ils ont été créés.  
  
     Comme indiqué dans le tableau suivant, les composants générés avec .NET Framework version 1.1 peuvent s’exécuter côte à côte avec les composants de la version 4, mais ils ne peuvent pas s’exécuter avec les composants de la version 2.0, 3.0 ni 3.5, car l’hébergement côte à côte n’est pas disponible pour ces versions.  
  
    |Version du .NET Framework|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Non applicable|Non |Oui|  
    |2.0 - 3.5|Non |Non applicable|Oui|  
    |4|Oui|Oui|Non applicable|  
  
> [!NOTE]
> Les versions 3.0 et 3.5 du .NET Framework sont générées de façon incrémentielle sur la version 2.0 et n’ont pas besoin de fonctionner côte à côte. Il s’agit fondamentalement de la même version.  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a>Scénarios d’hébergement côte à côte courants  
  
- **Scénario 1 :** application native qui utilise des composants COM créés avec des versions antérieures du .NET Framework.  
  
     .NET Versions-cadre installées: Le cadre .NET 4 et toutes les autres versions du cadre .NET utilisés par les composants COM.  
  
     Que faire : dans ce scénario, ne faites rien. Les composants COM s’exécuteront avec la version du .NET Framework avec laquelle ils ont été inscrits.  
  
- **Scénario 2**: Application gérée construite avec le .NET Framework 2.0 SP1 que vous préféreriez exécuter avec le cadre .NET 2.0, mais sont prêts à fonctionner sur le cadre .NET 4 si la version 2.0 n’est pas présente.  
  
     .NET Versions-cadre installées : Une version antérieure du cadre .NET et du cadre .NET 4.  
  
     Que faire : dans le [fichier de configuration de l’application](../configure-apps/index.md) dans le répertoire de l’application, utilisez l’[élément \<startup>](../configure-apps/file-schema/startup/startup-element.md) et l’[élément \<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) défini comme suit :  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Scénario 3 :** Application native qui utilise des composants COM construits avec des versions antérieures du cadre .NET que vous souhaitez exécuter avec le cadre .NET 4.  
  
     .NET Versions-cadre installées : Le cadre .NET 4.  
  
     Que faire : dans le fichier de configuration de l’application dans le répertoire de l’application, utilisez l’élément `<startup>` avec l’attribut `useLegacyV2RuntimeActivationPolicy` défini sur `true` et l’élément `<supportedRuntime>` défini comme suit :  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre un hôte COM non managé qui exécute un composant COM managé à l’aide de la version du .NET Framework dans laquelle le composant a été compilé.  
  
 Pour exécuter l’exemple suivant, compilez et inscrivez le composant COM managé suivant avec .NET Framework 3.5. Pour inscrire le composant, dans le menu **Projet**, cliquez sur **Propriétés**, sur l’onglet **Générer**, puis cochez la case **Inscrire pour COM Interop**.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 Compilez l’application C++ non managée suivante, ce qui active l’objet COM créé par l’exemple précédent.  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [\<start-up> Element](../configure-apps/file-schema/startup/startup-element.md)
- [\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)
