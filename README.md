# Progress 

## SPH
**veskery kod v tomto repozitari** [sph-mountain-waves](https://github.com/moschehaus/sph-mountain-waves)
- [x] zavedeni adaptivni artificialni viskozity
- [x] zavedeni variabilni smoothing length
    - [x] zpresneni pomoci Newtona
- [x] pokus o alternativni formulaci (*pressure-entropy*) ala Hopkins
- [ ] pokus o well-balancovani SPH schematu
- [x] experimentovani s ruznymi formulacemi: perturbace skrze WCSPH, vse skrze Hopkinse,...
- [x] monitorovani energie a obecne vylepseni diagnostiky
- [x] prepis *multi-mass distribution* na *single-mass distribution*
- [x] prechod k exponencialnimu pocatecnimu rozdeleni
- [ ] implementace okrajovych podminek:
    - [ ] zkvalitneni hranice
    - [ ] dolni podminka: *noslip* ci *freeslip*?
    - [ ] vtok: 
    - [ ] vytok: periodicke?
    - [ ] horni podminka: Rayleigh?

### Formulace
- **klasicke WCPSH**: plna formulace, diskretizace rovnice kontinuity
- **well balanced WCPSH**: stepeni na pozadi + perturbaci, diskretizace rovnice kontinuity
- **klasicky Hopkins**: plna formulace, adaptivni delka
- **: well balanced Hopkins*: $a' = a - a_0,$ adaptivni delka
***
- **WCSPH Hopkins**?: advekce entropie, ale interakce dle WCSPH
- **θ-Hopknis**?: Hopkinsova entropy-like variable $A$ by melo byt mozne vyjadrit pomoci potencialove teploty θ, ktera se ma taky zachovovat

## Trixi
**veskery kod v tomto repozitari** [sph-mountain-waves](https://github.com/moschehaus/trixi-mountain-waves)

## Lagrangian Voronoi

# Konzultace s P.S.
- existuji i *nehydrostaticke modely* - **co to je?**
- simulace IGW neni jedine, co by mohlo byt zajimave:
    - drag (ci obecne silove pusobeni) na prekazku
    - rychlostni pole na zavetrne strane kopce
    - (*nejaka*) hustota toku hybnosti
- vysledky se zpracovavaji vzhledem k nejakemu nondim cislu - inverzni Froudovo
- *umi dodat mnoho dat pro srovnani*

# AI acknowledgment

AI writing and language tools — specifically Writefull and Claude (Anthropic) — were used for auxiliary tasks including proofreading, prose checking, and code and TeX debugging, as well as for the preparation of figures in Makie.jl and TikZ. All scientific content, numerical implementations, and analytical conclusions are the author's own work.
