---
title: Code transparent de sécurité, niveau 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 8f232a7724ad831818627cbfc2845ea808a3fcfd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215805"
---
# <a name="security-transparent-code-level-1"></a>Code transparent de sécurité, niveau 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 La transparence permet aux développeurs d'écrire des bibliothèques .NET Framework plus sûres qui exposent les fonctionnalités à du code de niveau de confiance partielle. La transparence de niveau 1 a été introduite dans le .NET Framework version 2.0 et a été essentiellement utilisée en interne chez Microsoft. À partir du .NET Framework 4, vous pouvez utiliser la [transparence de niveau 2](security-transparent-code-level-2.md). Toutefois, la transparence de niveau 1 a été conservée afin que vous puissiez identifier le code hérité qui doit s’exécuter avec les règles de sécurité antérieures.  
  
> [!IMPORTANT]
> Vous ne devez spécifier la transparence de niveau 1 qu'à des fins de compatibilité. Autrement dit, ne spécifiez le niveau 1 que pour du code développé avec le .NET Framework version 3.5 ou antérieure qui utilise <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ou qui n'utilise pas le modèle de transparence. Par exemple, utilisez la transparence de niveau 1 pour les assemblys du .NET Framework 2.0 qui autorisent les appels des appelants ayant un niveau de confiance partielle (APTCA). Pour le code développé pour le .NET Framework 4, utilisez toujours la transparence de niveau 2.  
  
 Cette rubrique contient les sections suivantes :  
  
- [Modèle de transparence de niveau 1](#the_level_1_transparency_model)  
  
- [Attributs de transparence](#transparency_attributes)  
  
- [Exemples de transparence de la sécurité](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Modèle de transparence de niveau 1  
 Quand vous utilisez la transparence de niveau 1, vous utilisez un modèle de sécurité qui sépare le code en méthodes transparentes de sécurité, critiques sécurisées et critiques de sécurité.  
  
 Vous pouvez marquer un assembly entier, certaines classes d'un assembly ou certaines méthodes d'une classe comme étant transparents de sécurité. Le code transparent de sécurité ne peut pas élever les privilèges. Cette restriction a trois conséquences :  
  
- Le code transparent de sécurité ne peut pas effectuer d'actions <xref:System.Security.Permissions.SecurityAction.Assert>.  
  
- Toute demande de liaison qui serait satisfaite par le code transparent de sécurité devient une demande complète.  
  
- Tout code non sécurisé (non vérifiable) qui doit s'exécuter dans du code transparent de sécurité provoque une demande complète pour l'autorisation de sécurité <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>.  
  
 Ces règles sont mises en application par le common language runtime (CLR) pendant l'exécution. Le code transparent de sécurité transmet toutes les exigences de sécurité du code qu’il rappelle à ses appelants. Les demandes qui transitent par le code transparent de sécurité ne peuvent pas élever les privilèges. Si une application de confiance basse appelle du code transparent de sécurité et génère une demande de privilège élevé, celle-ci est renvoyée au code de confiance basse et échoue. Le code transparent de sécurité ne peut pas arrêter la demande, car il ne peut pas effectuer d'actions d'assertion. Le même code transparent de sécurité appelé à partir de code de niveau de confiance totale débouche sur une demande qui aboutit.  
  
 Critique de sécurité est l’inverse de transparent de sécurité. Le code critique de sécurité s'exécute avec une confiance totale et peut effectuer toutes les opérations nécessitant des privilèges. Le code critique sécurisé est du code à privilèges qui a fait l'objet d'un audit de sécurité approfondi pour s'assurer qu'il n'autorise pas les appelants ayant un niveau de confiance partielle à utiliser des ressources auxquelles ils ne sont pas autorisés à accéder.  
  
 Vous devez appliquer la transparence explicitement. La majeure partie de votre code qui gère la manipulation des données et la logique peut être marquée comme étant transparente de sécurité, tandis que le code subsidiaire qui opère des élévations de privilèges est marqué comme étant critique de sécurité ou critique sécurisé.  
  
> [!IMPORTANT]
> La transparence de niveau 1 se limite à la portée de l'assembly ; il ne s'applique pas entre les assemblys. La transparence de niveau 1 a été principalement utilisée en interne par Microsoft à des fins d'audit de sécurité. Les types et membres critiques de sécurité au sein d'un assembly de niveau 1 sont accessibles au code transparent de sécurité des autres assemblys. Il est important d'effectuer des demandes de liaison pour bénéficier d'une confiance totale dans tous vos types et membres critiques de sécurité de niveau 1. Les types et membres critiques sécurisés doivent aussi vérifier que les appelants disposent des autorisations sur les ressources protégées auxquelles les types ou membres accèdent.  
  
 Pour assurer une compatibilité avec les versions antérieures du .NET Framework, tous les membres qui ne sont pas annotés avec des attributs de transparence sont considérés comme étant critiques sécurisés. Tous les types qui ne sont pas annotés sont considérés comme étant transparents. Il n'existe aucune règle d'analyse statique pour valider la transparence. Par conséquent, vous serez peut-être amené à déboguer les erreurs de transparence au moment de l'exécution.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Attributs de transparence  
 Le tableau suivant décrit les trois attributs que vous utilisez pour annoter votre code pour la transparence.  
  
|Attribut|Description|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Autorisé uniquement au niveau de l'assembly. Identifie tous les types et membres de l'assembly comme étant transparents de sécurité. L'assembly ne peut pas contenir de code critique de sécurité.|  
|<xref:System.Security.SecurityCriticalAttribute>|Quand il est utilisé au niveau de l'assembly sans la propriété <xref:System.Security.SecurityCriticalAttribute.Scope%2A>, identifie par défaut l'ensemble du code contenu dans l'assembly comme étant transparent de sécurité, mais indique que l'assembly peut contenir du code critique de sécurité.<br /><br /> Quand il est utilisé au niveau de classe, identifie la classe ou la méthode comme étant critique de sécurité, mais pas les membres de la classe. Pour faire en sorte que tous les membres soient critiques de sécurité, affectez à la propriété <xref:System.Security.SecurityCriticalAttribute.Scope%2A> la valeur <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Quand il est utilisé au niveau du membre, l'attribut s'applique uniquement à ce membre.<br /><br /> La classe ou le membre identifié comme étant critique de sécurité peut opérer des élévations de privilèges. **Important :**  Dans la transparence de niveau 1, les types et membres critiques de sécurité sont traités comme étant critiques sécurisés lorsqu’ils sont appelés à partir de l’extérieur de l’assembly. Vous devez protéger les types et les membres critiques de sécurité avec une demande de liaison pour la confiance totale afin d'éviter une élévation de privilèges non autorisée.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifie le code critique de sécurité auquel le code transparent de sécurité de l'assembly peut accéder. À défaut, le code transparent de sécurité ne peut pas accéder aux membres critiques de sécurité privés ou internes du même assembly. Cela aurait une influence sur le code critique de sécurité et pourrait occasionner des élévations de privilèges inattendues. Le code critique sécurisé doit subir un audit de sécurité rigoureux. **Remarque :**  Les types et membres critiques sécurisés doivent valider les autorisations des appelants pour déterminer si l’appelant est habilité à accéder aux ressources protégées.|  
  
 L'attribut <xref:System.Security.SecuritySafeCriticalAttribute> permet au code transparent de sécurité d'accéder aux membres critiques de sécurité du même assembly. Considérez le code transparent de sécurité et le code critique de sécurité de votre assembly comme séparés en deux assemblys. Le code transparent de sécurité ne serait pas en mesure de distinguer les membres privés ou internes du code critique de sécurité. De plus, l'accès à l'interface publique du code critique de sécurité faire généralement l'objet d'un audit. Vous ne trouveriez probablement pas logique qu'un état privé ou interne soit accessible en dehors de l'assembly ; vous préféreriez que l'état reste isolé. L'attribut <xref:System.Security.SecuritySafeCriticalAttribute> garantit l'isolation de l'état entre le code transparent de sécurité et le code critique de sécurité tout en offrant la possibilité de substituer l'isolation quand cela est nécessaire. Le code transparent de sécurité ne peut pas accéder au code critique de sécurité privé ou interne à moins que ces membres aient été marqués avec <xref:System.Security.SecuritySafeCriticalAttribute>. Avant d'appliquer <xref:System.Security.SecuritySafeCriticalAttribute>, auditez ce membre comme s'il était exposé publiquement.  
  
### <a name="assembly-wide-annotation"></a>Annotation à l'échelle de l'assembly  
 Le tableau suivant décrit les effets de l'utilisation d'attributs de sécurité au niveau de l'assembly.  
  
|Attribut d’assembly|État de l'assembly|  
|------------------------|--------------------|  
|Aucun attribut sur un assembly de niveau de confiance partielle|Tous les types et membres sont transparents.|  
|Aucun attribut sur un assembly de niveau de confiance totale (dans le Global Assembly Cache ou identifié comme étant de confiance totale dans le `AppDomain`)|Tous les types sont transparents et tous les membres sont critiques sécurisés.|  
|`SecurityTransparent`|Tous les types et membres sont transparents.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Tous les types et membres sont critiques de sécurité.|  
|`SecurityCritical`|Tout le code est transparent par défaut. Cependant, chaque type et membre individuel peut avoir d'autres attributs.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Exemples de transparence de la sécurité  
 Pour utiliser les règles de transparence du .NET Framework 2.0 (transparence de niveau 1), utilisez l'annotation d'assembly suivante :  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Si vous voulez rendre un assembly entier transparent pour indiquer qu'il ne contient pas de code critique et qu'il n'élève en aucune manière les privilèges, vous pouvez ajouter explicitement la transparence à l'assembly par le biais de l'attribut suivant :  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Si vous voulez combiner du code critique et du code transparent dans un même assembly, commencez par marquer l'assembly avec l'attribut <xref:System.Security.SecurityCriticalAttribute> pour indiquer que l'assembly peut contenir du code critique, comme suit :  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Si vous voulez effectuer des actions critiques de sécurité, vous devez marquer explicitement le code chargé d'effectuer l'action critique avec un autre attribut <xref:System.Security.SecurityCriticalAttribute>, comme illustré dans l'exemple de code suivant :  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 Le code précédent est transparent à l'exception de la méthode `Critical`, qui est marquée explicitement comme étant de sécurité critique. La transparence est le paramètre par défaut, même avec l'attribut <xref:System.Security.SecurityCriticalAttribute> au niveau de l'assembly.  
  
## <a name="see-also"></a>Voir aussi

- [Code transparent de sécurité, niveau 2](security-transparent-code-level-2.md)
- [Modifications de sécurité](../security/security-changes.md)
