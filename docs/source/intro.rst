.. highlight:: shell

============
Introduction
============

The Regulated Ecosystem Model, version 2, (REcoM-2) describes the
biogeochemistry in the ocean with a relatively simple ecological model
including two phytoplankton functional types (diatoms and non-diatoms), one
zooplankton and one detritus compartment, and inorganic and organic
forms of the main nutrients (Figure \ref{images/Figure1.eps}). Some emphasis is put on phytoplankton
physiology, which is described in a way that allows for changes in
cellular stoichiometry (N:C:Chl:Si for diatoms and N:C:Chl for
non-diatoms, respectively). All in all, the model solves mass balance
equations for 21 tracers, which are described by equations of the type

.. math::
   \frac{\partial{A}}{\partial{t}} =-(\mathbf{U} + \mathbf{w})\cdot \mathbf{\nabla} A + 
   \mathbf{\nabla} \cdot \left( \kappa \mathbf{\nabla} A \right) + S(A)

where :math:`\mathbf{A}` is the volumetric concentration of a tracer, :math:`\mathbf{U}` is the
three-dimensional advection velocity and :math:`\kappa` is the diffusivity,
both supplied by the physical circulation model. The sinking velocity of particles 
:math:`\mathbf{w} = (0,0,w)` increases linearly with depth for detritus and has
a constant value for phytoplankton and diatoms.

:math:`\mathbf{S(A)}` are the biogeochemical sources or sinks of the
tracer :math:`\mathbf{A}` and are described in detail, for any of the tracers, in the
following.  

.. figure:: images/Figure1.png
   :scale: 40 %
   :alt: Schematic sketch of the ecosystem model REcoM-2.
   :align: center
 
   *Schematic sketch of the ecosystem model REcoM-2. The 21 tracers can be grouped (indicated by boxes) into dissolved nutrients and carbonate system parameters (upper left), phytoplankton (center), zooplankton (upper right), detritus (lower right), and dissolved organic material (lower left). Source and sink terms are depicted by arrows, short arrows denote exchange with atmosphere and sediments. Not shown: sediments also release alkalinity, inorganic nutrients and dissolved organic matter.*

      
Carbonate chemistry
===================
.. _sec_carbchem:

Dissolved inorganic carbon (:math:`\mathrm{DIC}`)
-------------------------------------------------
The balance of :math:`\mathrm{DIC}` is affected by a number of processes; sources for
DIC are respiration by nanophytoplankton (:math:`phy`), diatoms (:math:`dia`) and
heterotrophs (:math:`het`), remineralization of dissolved organic carbon
(:math:`\mathrm{DOC}`) and dissolution of calcitic detritus (:math:`det`). Sinks are carbon
fixation by primary producers and the formation of calcium carbonate
(:math:`Z`). In addition, sea-air flux of :math:`CO_2` (:math:`F_{\mathrm{C}}`) leads to an
exchange of carbon with the atmosphere, depending on the partial
pressure difference of :math:`CO_2` between ocean and atmosphere. This
exchange is treated separately as boundary condition in section

.. math::
   \begin{split}
   S(\mathrm{DIC}) = & \;(r_{phy} - p_{phy}) \cdot \mathrm{C}_{phy} + (r_{dia} - p_{dia})
   \cdot \mathrm{C}_{dia} \\ &\; + r_{het} \cdot \mathrm{C}_{het} + \rho_{\mathrm{DOC}} \cdot f_T
   \cdot \mathrm{DOC}\\ &\; + \lambda \cdot \mathrm{CaCO}_{3 \,det} - Z
   \end{split}
 
See section \ref{sec:phy} for details on photosynthesis (:math:`p`) and
phytoplankton respiration (:math:`r`) rates. :math:`\mathrm{C}_{phy}`, :math:`\mathrm{C}_{dia}` and
:math:`\mathrm{C}_{het}` refer to carbon biomass of nanophytoplankton, diatoms and
heterotrophs, respectively. See section \ref{sec:het} for the
formulation of the heterotrophic respiration rate (:math:`r_{het}`) and
section \ref{sec:dom} for the DOC remineralization term (:math:`\rho_{\mathrm{DOC}} \cdot f_T \cdot \mathrm{DOC}`). 
The calcite dissolution rate (:math:`\lambda`) is defined
in Eq. \ref{eq:calcdiss} and the calcification flux (:math:`Z`) in
Eq. \ref{eq:calcif}.


Total Alkalinity (:math:`\mathrm{TA}`) 
--------------------------------------

The alkalinity balance is
determined by processes co-occurring with primary production and
remineralization of dissolved organic matter. Alkalinity is increased by nitrogen assimilation and reduced by remineralization of dissolved
organic nitrogen (DON). The contribution of phosphate
assimilation and remineralization to alkalinity is taken into account
by assuming a constant Redfield ratio (16:1) relating :math:`\mathrm{DON}` to
dissolved organic phosphorous (:math:`\mathrm{DOP}`). Further, alkalinity is reduced
during calcification and increased during
dissolution of :math:`CaCO_3`.

.. math::
   \begin{split}
   S(\mathrm{TA}) = & \;(1 + \frac{1}{16}) \cdot ( a^N_{phy} \cdot \mathrm{C}_{phy} +
   a^N_{dia} \cdot \mathrm{C}_{dia}- \rho_{\mathrm{DON}} \cdot f_T \cdot \mathrm{DON} )     \\ 
   &+ 2\;(\lambda \cdot \mathrm{CaCO}_{3 \,det} - Z)
   \end{split}

See section \ref{sec:phy} for details on the nitrogen assimilation
rates (:math:`a^N_{phy}` and :math:`a^N_{dia}`), and section \ref{sec:dom} for the
:math:`\mathrm{DON}` remineralization term (:math:`\rho_{\mathrm{DON}} \cdot f_T \cdot \mathrm{DON}`).
The calcification flux (:math:`Z`) is defined in Eq. \ref{eq:calcif} and the dissolution rate of :math:`CaCO_3` (:math:`\lambda`) in Eq. \ref{eq:calcdiss}.

Nutrients
=========
.. _sec_nuts:

Dissolved Inorganic Nitrogen (:math:`\mathrm{DIN}`)
---------------------------------------------------

:math:`\mathrm{DIN}` in the model is the sum of the concentrations of nitrate,
nitrite and ammonia. The :math:`\mathrm{DIN}` pool in the water column is reduced
when nanophytoplankton and diatoms take up :math:`\mathrm{DIN}` and build it into
their cells. Remineralization of :math:`\mathrm{DON}` is a source for :math:`\mathrm{DIN}`.


.. math::
   \begin{split}
   S(\mathrm{DIN}) = &\; - a^N_{phy} \cdot \mathrm{C}_{phy} - a^N_{dia} \cdot \mathrm{C}_{dia} +
   \rho_{\mathrm{DON}} \cdot f_T \cdot \mathrm{DON}  
   \end{split}


See section \ref{sec:phy} for details on the nitrogen assimilation
rates (:math:`a^N_{phy}` and :math:`a^N_{dia}`) and section \ref{sec:dom} for an
explanation of the temperature dependent :math:`\mathrm{DON}` remineralization. 


Dissolved Silicate (:math:`\mathrm{DSi}`)
-----------------------------------------

Silicon cycles between dissolved silicic acid, or silicate :math:`\mathrm{DSi}`, and
the biogenic silica in diatoms :math:`\mathrm{Si}_{dia}` and detritus
(:math:`\mathrm{Si}_{det}`). Silicate in the water column is drawn down by silicate
assimilation and returned via degradation of detritus silica.

.. math::
   \begin{split}
   S(\mathrm{DSi}) = &\; - a^{Si}_{dia} \cdot \mathrm{C}_{dia} + \rho^T_{Si} \cdot \mathrm{Si}_{det}
   \end{split}

See section \ref{sec:phy} for the definition of the silicate
assimilation rate (:math:`a^{Si}_{dia}`). The temperature-dependent
dissolution rate of silica :math:`\rho^T_{Si}` is defined in
Eq.\ \ref{eq:sidiss}.


Dissolved Iron (:math:`\mathrm{DFe}`)
-------------------------------------

Dissolved iron is treated in the model like in \citet{Parekh2004},
i.e. it is considered the sum of the concentrations of "free"
(i.e.\ inorganically bound) iron :math:`\mathrm{Fe}'` and organically
complexed iron :math:`\mathrm{FeL}`. The partitioning into these two types
is assumed to be in chemical equilibrium always, and is calculated at
each timestep by solving the law of mass action for a reaction
:math:`\mathrm{Fe}' + \mathrm{L} \leftrightarrows \mathrm{FeL}` with
:math:`\mathrm{L}` being the free ligand concentration, assuming both a
constant conditional stability constant :math:`K_{FeL} = \mathrm{Fe}' \cdot
L / FeL` and total ligand concentration :math:`\mathrm{L}_T = \mathrm{L} +
\mathrm{FeL}`.

Dissolved iron is drawn down in concert with photosynthesis by
nanophytoplankton and diatoms and by scavenging of free Fe. For the
scavenging we assume that it is proportional to detritus carbon, which
we take as a proxy for the mass of sinking particles. Iron is
released during  respiration of phytoplankton and heterotrophs,
remineralization of :math:`\mathrm{DOC}`, and excretion of heterotrophs.
Degraded iron is directly remineralized to dissolved iron. For all
these processes, we assume a constant iron:carbon ratio (:math:`q^{Fe}`).

.. math::
   \begin{split}
   S(\mathrm{DFe}) = &\; q^{Fe} \cdot ( (r_{phy} -
   p_{phy} ) \cdot \mathrm{C}_{phy} + (r_{dia} - p_{dia} ) \cdot \mathrm{C}_{dia} + (r_{het}
   + \epsilon^C_{het}) \cdot \mathrm{C}_{het}\\ 
   &\; + \rho_{\mathrm{DOC}} \cdot f_T \cdot \mathrm{DOC}) - \kappa^{scav}_{Fe} \cdot
   \mathrm{C}_{det} \cdot \mathrm{Fe}'
   \end{split}

See section \ref{sec:phy} for an explanation of phytoplankton photosynthesis (:math:`p`) and respiration (:math:`r`) rates and section \ref{sec:het} for the heterotrophic
respiration (:math:`r_{het}`) and carbon excretion rate (:math:`\epsilon^C_{het}`). The DOC remineralization term is described in section \ref{sec:dom}. 

Phytoplankton
=============
.. _sec_phy:

The equations for the two classes of phytoplankton are based on a
slightly modified version of the physiological model by
\citet{Geider1998} that has been amended by non-physiological
mortality terms, namely grazing and aggregation loss to sinking
detritus \citep{Schartau2007}. For diatoms an additional equation
describing the formation and loss of biogenic silica in the diatom
frustule has been added by \citet{Hohn2009}.

All physiological rates, such as the photosynthesis and assimilation rates 
depend on cell quota in the formulation of \citet{Geider1998}. These are defined as the intracellular ratios of N:C, Chl:C and Si:C:

.. math::
   \begin{split}
   q = \frac{\mathrm{N}}{\mathrm{C}};\;\;\; q^{Si} &= \frac{\mathrm{Si}}{\mathrm{C}};\;\;\; q^{Chl} = \frac{\mathrm{Chl}}{\mathrm{C}};\;\;\;
   \end{split}
 
In addition quota are used to convert biomass in terms of carbon or nitrogen to Fe, Si, Chl or :math:`CaCO_3`:

.. math::
   q^{Fe} = \frac{\mathrm{Fe}}{\mathrm{C}} \;\;\;
   q^{Si:N} = \frac{\mathrm{Si}}{\mathrm{N}};\;\;\; q^{Chl:N} = \frac{\mathrm{Chl}}{\mathrm{N}};\;\;\;q^{CaCO_3:N} = \frac{\mathrm{CaCO_3}}{\mathrm{N}}; 

Nitrogen pool (:math:`\mathrm{N}_{phy}` and :math:`\mathrm{N}_{dia}`)
---------------------------------------------------------------------

The nitrogen pool in nanophytoplankton and diatoms is built up by the
assimilation of nitrogen, which is assumed proportional to carbon biomass.
Metabolic processes lead to excretion of biogenic nitrogen to the
:math:`\mathrm{DON}` pool.  At high intracellular N:C ratios (:math:`q`), we assume that this
excretion is downregulated.  Aggregation and grazing by zooplankton
transfer nitrogen to the detritus and zooplankton pools:

.. math::
   \begin{split}
   S(\mathrm{N}_{phy}) = &\;a^N_{phy} \cdot \mathrm{C}_{phy} - (\epsilon^N_{phy} \cdot
   f^{lim}_{phy} + g) \cdot \mathrm{N}_{phy}  - G_{phy} 
   \end{split}

.. math::
   \begin{split}
   S(\mathrm{N}_{dia}) = &\;a^N_{dia} \cdot \mathrm{C}_{dia} -
   (\epsilon^N_{dia} \cdot f^{lim}_{dia} + g) \cdot \mathrm{N}_{dia} - G_{dia} 
   \end{split}

See section \ref{sec:het} for a description of the grazing formulation
(:math:`G_{phy}` and :math:`G_{dia}`).
The carbon-specific nitrogen uptake rate depends on the maximum
photosynthetic rate (:math:`p_{phy}^{max}` and :math:`p_{dia}^{max}`,
Eq. \ref{eq:p^{max}_{phy}}, Eq. \ref{eq:p^{max}_{dia}}), which is
converted to nitrogen units by multiplication with an optimal N:C
uptake ratio (:math:`\sigma^N_{phy}` and :math:`\sigma^N_{dia}`). Nitrogen uptake
rates are further affected by the intracellular nitrogen status :math:`q`
through :math:`f^{lim}_{phy}` and :math:`f^{lim}_{dia}`, (see
Eq. \ref{eq:f^{lim}_{phy}} and Eq. \ref{eq:f^{lim}_{dia}}) and by
extracellular nitrogen concentrations through an assumed 
Michaelis-Menten uptake kinetics.

.. math::
   \begin{split}
   a_{phy}^{N} = p_{phy}^{max} \cdot \sigma_{phy}^N \cdot
   f^{lim}_{phy} \cdot (\frac{\mathrm{DIN}}{\mathrm{DIN} + K_{phy}^{\mathrm{N}}}) 
   \end{split}

.. math::
   \begin{split}
   a_{dia}^{N} = p_{dia}^{max} \cdot \sigma_{dia}^N \cdot
   f^{lim}_{dia} \cdot (\frac{\mathrm{DIN}}{\mathrm{DIN} + K_{dia}^{\mathrm{N}}}) 
   \end{split}

As in the model by \citet{Geider1998}, both the limiting functions
(:math:`f^{lim}_{phy}` and :math:`f^{lim}_{dia}`) for nitrogen assimilation and
excretion rates :math:`\epsilon^N_{phy}` and :math:`\epsilon^N_{dia}` are
treated as functions of the intracellular nitrogen status (i.e., N:C ratios
:math:`q`). 

The mathematical form of how this regulation is described has
no specific basis in physiology. In a slight change against the model
by \citet{Geider1998} we use a uniform general limitation function
for all types of quota regulation, which is given by

.. math::
   \begin{split}
   f(q_1,q_2,\theta) = \left\{ 
   \begin{array}{lll}
   1 - \exp(-4 \theta (q_1-q_2)^2 ) & \mathrm{if} & q_1 < q_2\\
   0          & \mathrm{if} & q_1 \ge q_2
   \end{array}
   \right.
   \end{split}

This regulation function is close to one for :math:`q_1 << q_2`, but tends
to zero for :math:`q_1` \to :math:`q_2`; :math:`\theta` is a dimensionless constant that
determines how close :math:`q_1` and :math:`q_2` have to be for a significant
decrease of :math:`f`.

With this function we can now formulate the functions limiting nitrogen
assimilation as

.. math::
   \begin{split}
   f^{lim}_{phy} = f(q_{phy},q_{phy\,max},\theta_{max}) 
   \end{split}

and

.. math::
   \begin{split}
   f^{lim}_{dia} = f(q_{dia},q_{dia\,max},\theta_{max}) 
   \end{split}

The aggregation rate (:math:`g`) is assumed to be proportional to the
abundance of phytoplankton and detritus: 

.. math::
   \begin{split}
   g = \phi_{phy} \cdot \mathrm{N}_{phy} + \phi_{phy} \cdot
   \mathrm{N}_{dia} + \phi_{det} \cdot \mathrm{N}_{det}
   \end{split}

The constants :math:`\phi_{phy}`  and :math:`\phi_{det}` are specific aggregation
rates (i.e. per unit biomass per unit time) of phytoplankton and
detritus, respectively, which reflect the roles of phytoplankton and
detritus in the aggregation processes.

Carbon pool (:math:`\mathrm{C}_{phy}` and :math:`\mathrm{C}_{dia}`)
-------------------------------------------------------------------

The carbon biomass of nanophytoplankton and diatoms increases as a
result of carbon assimilation during photosynthesis. Loss terms
include excretion (:math:`\epsilon`) of :math:`\mathrm{DOC}`, which is limited by the
availablity of proteins as in the nitrogen pool, respiration (:math:`r`),
aggregation (:math:`g`), and grazing (:math:`G`).

.. math::
   \begin{split}
   \label{C_{phy}}
   S(\mathrm{C}_{phy}) = &\;(p_{phy}  - \epsilon^C_{phy} \cdot f^{lim}_{phy} -
   r_{phy} - g) \cdot \mathrm{C}_{phy} - \frac{1}{q_{phy}}Ê\cdot G_{phy}
   \end{split}

.. math::
   \begin{split}
   \label{C_{dia}}
   S(\mathrm{C}_{dia}) = &\;(p_{dia}  - \epsilon^C_{dia}  \cdot f^{lim}_{dia} -
   r_{dia} - g) \cdot \mathrm{C}_{dia} -  \frac{1}{q_{dia}} \cdot G_{dia} 
   \end{split}

Grazing (:math:`G`) is calculated on the basis of nitrogen biomass and
converted to carbon using the intracellular N:C ratio (:math:`q_{phy}`, :math:`q_{dia}`). See section \ref{sec:het} for the grazing
formulation, Eq. \ref{eq:g} for the aggregation rate :math:`g` and Eq. \ref{eq:f^{lim}_{phy}} and
Eq. \ref{eq:f^{lim}_{dia}} for the limiter functions for the carbon
excretion rates :math:`\epsilon^C_{phy}` and :math:`\epsilon^C_{dia}`.

The photosynthetic rate (:math:`p_{phy}` and :math:`p_{dia}`) is a saturating
function of the photosynthetically active radiation (:math:`PAR`). The
saturating light level is affected by the internal chlorophyll status
of the cells. The initial slope of the photosynthesis-irradiance-curve
is obtained by multiplication of the light harvesting efficiency per
chlorophyll (:math:`\alpha`) with the intracellular chlorophyll to carbon
ratio (:math:`q^{Chl}`).

.. math::
   \label{eq:p_{phy}}
   p_{phy} = p^{max}_{phy} \cdot \left( 1 - \exp \left( -\alpha_{phy} \cdot
    q^{Chl}_{phy} \cdot PAR / p^{max}_{phy} \right) \right) 

.. math::
   \label{eq:p_{dia}}
   p_{dia} =p^{max}_{dia} \cdot \left( 1 - \exp \left( -\alpha_{dia} \cdot
    q^{Chl}_{dia} \cdot PAR / p^{max}_{dia} \right) \right) 


The apparent maximum photosynthetic rates (:math:`p^{max}_{phy}` and
:math:`p^{max}_{dia}`) are based on the true constant maximum photosynthetic
rates :math:`\mu^{max}_{phy}` and :math:`\mu^{max}_{dia}`, but vary with the
metabolic state of the cell, external dissolved Fe concentration and
temperature: 

.. math::
   \label{eq:p^{max}_{phy}}
   \begin{split}
   p^{max}_{phy} = &\;\mu^{max}_{phy} \cdot f_{T} \cdot \min( l^{Fe}_{phy}, l^{N}_{min})
   \end{split}

.. math::
   \label{eq:p^{max}_{dia}}
   \begin{split}
   p^{max}_{dia} = &\;\mu^{max}_{dia} \cdot f_{T} \cdot \min( l^{Fe}_{dia}, l^{N}_{min}, l^{Si}_{min})
   \end{split}

Growth, as most metabolic processes is faster at higher temperatures. We
parameterize this by multiplication of the maximum growth rate
with an Arrhenius function :math:`f_T` of the local temperature (:math:`T` in Kelvin),
relative to a reference temperature :math:`T_{ref}`: 

.. math::
   \label{eq:arr}
   f_T = \exp \left(- 4500 \cdot \left( \frac{1}{T}- \frac{1}{T_{ref}}\right) \right)

Growth-limitation by iron is represented by a Michaelis-Menten term

.. math::
   \label{eq:limFe}
   l^{Fe}_{phy} = \frac{\mathrm{DFe}}{\mathrm{DFe} + K^{Fe}_{phy}}, \;\;\; l^{Fe}_{dia} = \frac{\mathrm{DFe}}{\mathrm{DFe} + K^{Fe}_{dia}}

while nitrogen limitation of nanophytoplankton and diatoms is modeled as a
function of the intracellular nitrogen quota :math:`q`, with growth
ceasing completely at a minimum quota :math:`q_{min}` 

.. math::
   \label{eq:l_{minNC}}
   \begin{split}
   l^N_{min} = f(q_{min},q,\theta_{min})
   \end{split}

For diatoms, photosynthesis is also downregulated if the cellular Si:C
ratio (:math:`q^{Si}`) approaches a minimum ratio :math:`q^{Si}_{min}`

.. math::
   \label{eq:l_{minSiC}}
   \begin{split}
   l^{Si}_{min} = f(q_{min}^{Si},q^{Si},\theta_{min}^{Si})
   \end{split}

:math:`\theta_{min}` and :math:`\theta_{min}^{Si}` are dimensionless
constants which regulate the steepness of the quota-growth relation (see Eq. \ref{eq:lim}). 


The respiration rates (:math:`r_{phy}` and :math:`r_{dia}`) represent the
sum of maintenance metabolic losses and the costs of biosynthesis,
which are proportional to the rates of nutrient assimilation: 
 
.. math::
   \label{eq:r_{phy}}
   \begin{split}
   r_{phy} = \eta_{phy} \cdot f^{lim}_{phy} + \zeta^{N} \cdot a^{N}_{phy}
   \end{split}

.. math::
   \label{eq:r_{dia}}
   \begin{split}
   r_{dia} = \eta_{dia} \cdot f^{lim}_{dia} + \zeta^{N} \cdot
   a^{N}_{dia} + \zeta^{Si} \cdot a^{Si}_{dia} 
   \end{split}

See Eq. \ref{eq:f^{lim}_{phy}} and Eq. \ref{eq:f^{lim}_{dia}} for the
limiting functions :math:`f^{lim}` of the constant maintenance respiration
rates :math:`\eta_{phy}` and :math:`\eta_{dia}`. :math:`\zeta` denotes the cost for
nutrient uptake and synthesis of cellular machinery in mol carbon per
mol of nitrogen and silicon, respectively. See
Eq. \ref{eq:a_{phy}^{N}}, Eq. \ref{eq:a_{dia}^{N}} and
Eq. \ref{eq:a^{Si}_{dia}} for details of the nutrient assimilation
rates.

Chlorophyll (:math:`\mathrm{Chl}_{phy}` and :math:`\mathrm{Chl}_{dia}`)
-----------------------------------------------------------------------

Chlorophyll synthesis is modeled as a function of irradiance and of nitrogen
assimilation. Chlorophyll is degraded with a fixed rate (:math:`d^{Chl}`), and lost via aggregation (:math:`g`) and grazing (:math:`G`). 

.. math::
   \label{Chl_{phy}}
   \begin{split}
   S(\mathrm{Chl}_{phy}) = &\;s_{phy}  \cdot \mathrm{C}_{phy}
   - (d^{Chl}_{phy} + g) \cdot \mathrm{Chl}_{phy} - G_{phy} \cdot q^{Chl:N}_{phy} 
   \end{split}

.. math::
   \label{Chl_{dia}}
   \begin{split}
   S(\mathrm{Chl}_{dia}) = &\;s_{dia}  \cdot \mathrm{C}_{dia}
   - (d^{Chl}_{dia} + g) \cdot \mathrm{Chl}_{dia} - G_{dia} \cdot q^{Chl:N}_{dia} 
   \end{split}

See Eq. \ref{eq:g} for the aggregation rate
(:math:`g`). The grazing flux :math:`G` in terms of nitrogen biomass is converted
to chlorophyll using the intracellular Chl:N ratio (:math:`q^{Chl:N}`).

The chlorophyll synthesis rate :math:`s` is assumed to be proportional to
the nitrogen assimilation rate, as nitrogen is required for the
synthesis of chlorophyll, for light harvesting and in the
photosynthetic apparatus: 

.. math::
   \label{s_{phy}}
   \begin{split}
   s_{phy} = a _{phy}^{N} \cdot q_{phy\;max}^{Chl:N} \cdot 
   \min\left( 1, \frac{p_{phy}}{\alpha_{phy} \cdot q^{Chl}_{phy} \cdot
   PAR} \right) 
   \end{split}

.. math::
   \label{s_{dia}}
   \begin{split}
   s_{dia}= a _{dia}^{N} \cdot q_{dia\,max}^{Chl:N} \cdot 
   \min\left( 1, \frac{p_{dia}}{\alpha_{dia} \cdot q^{Chl}_{dia} \cdot
   PAR} \right) 
   \end{split}

The carbon-specific nitrogen assimilation rates (:math:`a_{phy}^{N}` and
:math:`a_{dia}^{N}`, see Eq. \ref{eq:a_{phy}^{N}} and \ref{eq:a_{dia}^{N}})
are converted to chlorophyll units by multiplication with a constant
maximum Chl:N ratio (:math:`q_{phy\;max}^{Chl:N}`) and
(:math:`q_{dia\,max}^{Chl:N}`). The regulation term 
:math:`\min(1, p_{phy} / (\alpha_{phy} \cdot q^{Chl}_{phy} \cdot PAR) )`
reflects the ratio of enery assimilated to energy absorbed; it
increases under low irradiance and declines as photosynthesis becomes
light saturated and/or nutrient limited. 
See Eq. \ref{eq:p_{phy}}
and Eq. \ref{eq:p_{dia}} for the descriptions of photosynthesis rate 
:math:`p_{phy}` and :math:`p_{dia}`.  

Diatom silica pool (:math:`\mathrm{Si}_{dia}`) 
----------------------------------------------

The silica frustule of diatoms is built through silicate assimilation. Any term that leads to
a decrease in N-biomass through excretion, grazing or aggregation, on
the other hand, leads to a corresponding transfer of silica to the
detritus silica pool.
 
.. math::
   \label{Si_{dia}}
   \begin{split}
   S(\mathrm{Si}_{dia}) = &\; a^{Si}_{dia} \cdot \mathrm{C}_{dia} - (\epsilon^{N}_{dia}
   \cdot f^{lim}_{dia} + g) \cdot \mathrm{Si}_{dia} - G_{dia} \cdot q^{Si:N}_{dia} 
   \end{split}

The intracellular Si:N ratio :math:`q^{Si:N}_{dia}` is used to convert the
grazing flux :math:`G_{dia}` (Eq. \ref{eq:Gdia}) to the corresponding loss in biogenic silica. See
Eq. \ref{eq:g} for the aggregation rate (:math:`g`) and
Eq. \ref{eq:f^{lim}_{dia}} for the function (:math:`f^{lim}_{dia}`) limiting
the excretion rate (:math:`\epsilon^N_{dia}`).

Silicate assimilation is treated as a relatively independent metabolic
pathway. Here, silicon uptake is formulated as Michaelis-Menten
kinetics. The maximum silicon uptake rate is calculated from the
constant maximum photosynthesis rate (:math:`\mu^{max}_{dia}`) by
multiplying it with a constant maximum Si:C uptake ratio
(:math:`\sigma_{dia}^{Si}`), and is regulated by intracellular N:C and Si:C
ratios (:math:`f^{lim}_{dia}` and :math:`f^{Si}_{dia}`) and temperature
(:math:`f_{T}`). Silicon uptake is reduced when cellular Si:C ratios (:math:`q^{Si}`)
approach the maximum Si:C ratio
(:math:`q_{max}^{Si}`). :math:`\theta_{max}^{Si}` is a dimensionless
constant which is used to regulate the slope.  

.. math::
   \label{eq:a^{Si}_{dia}}
   \begin{split}
   a^{Si}_{dia} = \mu^{max}_{dia} \cdot  \sigma_{dia}^{Si} \cdot f_{T}
   \cdot f^{lim}_{dia} \cdot f^{Si}_{dia} \cdot (\frac{\mathrm{DSi}}{\mathrm{DSi} +
   K_{dia}^{\mathrm{Si}}}) 
   \end{split}

.. math::
   \label{eq:f^{Si}_{dia}}
   \begin{split}
   f^{Si}_{dia} = f(q^{Si},q_{max}^{Si},\theta_{max}^{Si})
   \end{split}

Iron limitation shows an indirect influence on silicate assimilation
via variable intracellular Si:N:C ratios by affecting the assimilation
of nitrogen and carbon. 
See Eq. \ref{eq:f^{lim}_{dia}} for the description of the limiting
function :math:`f^{lim}_{dia}` and Eq. \ref{eq:arr} for the definition of
the temperature dependence :math:`f_{T}`. 

Calcite pool (:math:`\mathrm{CaCO}_{3 \, phy}`)
-----------------------------------------------

In REcoM-2, the formation of biogenic calcium carbonate is limited to
phytoplankton (i.e.\ coccolithophorids) which are assumed to form a
constant fraction of the non-diatom phytoplankton. Formation of
:math:`CaCO_3` by heterotrophs, such as foraminifera or pteropods is
neglected. Biogenic :math:`CaCO_3` is transformed into detritus :math:`CaCO_3`
along with organic matter excretion, respiration, aggregation and
grazing.

.. math::
   \label{CaCO3}
   \begin{split}
   S(\mathrm{CaCO}_{3\,phy}) = &\; Z - (\epsilon^C_{phy}  \cdot f^{lim}_{phy} +
   r_{phy} + g ) \cdot \mathrm{CaCO}_{3\,phy} - G_{phy} \cdot
   q^{CaCO_3:N}_{phy} 
   \end{split}

Calcification (:math:`Z`) is proportional to gross carbon fixation by
nanophytoplankton:
 
.. math::
   \label{eq:calcif}
   Z = \psi \cdot p_{phy} \cdot \mathrm{C}_{phy} 

$\psi$ is the calcite production ratio that incorporates the ratio of
calcium carbonate producers to total nanophytoplankton and the :math:`CaCO_3`:POC
ratio in coccolithophorids. The latter is assumed to be 1.  

See Eq. \ref{eq:f^{lim}_{phy}} for the function :math:`f^{lim}_{phy}`
limiting the excretion rate :math:`\epsilon^C_{phy}`. Nanophytoplankton photosynthesis (:math:`p_{phy}`)
respiration (:math:`r_{phy}`) and aggregation (:math:`g`) rates are defined
in Eq. \ref{eq:p_{phy}}, Eq. \ref{eq:r_{phy}} and Eq. \ref{eq:g}, respectively. The grazing flux :math:`G_{phy}` (Eq. \ref{eq:Gphy}) is
calculated in units of nitrogen biomass and converted to :math:`CaCO_3`
using the intracellular :math:`CaCO_3`:N ratio (:math:`q^{CaCO_3:N}_{phy}`). 

Heterotrophs
============
.. _sec_het:

Nitrogen pool (:math:`\mathrm{N}_{het}`)
----------------------------------------
Heterotrophic zooplankton increase their nitrogen pool via grazing,
and loose nitrogen through excretion of :math:`\mathrm{DON}` and a quadratic mortality term:

.. math::
   \label{hetN}
   \begin{split}
   S(\mathrm{N}_{het}) = &\; G \cdot \gamma - m_{het} \cdot \mathrm{N}_{het}^2 -
   \epsilon^N_{het} \cdot \mathrm{N}_{het} 
   \end{split}

A quadratic term is used for the mortality of heterotrophs (:math:`m_{het} \cdot \mathrm{N}_{het}^2`), and the
excretion rate :math:`\epsilon^{N}_{het}` transfers heterotrophic nitrogen
directly to the :math:`\mathrm{DON}` pool. 
The grazing efficiency :math:`\gamma` determines how much of the grazed
phytoplankton is built into heterotrophic biomass. We assume that
sloppy feeding and the formation of feces transfer
the remainder of the grazed phytoplankton directly to detritus.

The grazing on nanophytoplankton and diatoms is defined as:

.. math::
   \label{eq:G}
   \begin{split}
   G = \xi \cdot \frac{(\mathrm{N}_{phy} + \mathrm{N}_{dia}^{'})^2}{\varphi_{1} + (\mathrm{N}_{phy}
   + \mathrm{N}_{dia}^{'})^2} \cdot f_{T} \cdot \mathrm{N}_{het} 
   \end{split}

The grazing rate is calculated from a constant maximum grazing rate
(:math:`\xi`) by multiplication with a sigmoidal dependency of nutritional
intake to resource density with half-saturation constant
:math:`\varphi_{1}`. It depends on temperature following the same
relationship as for phytoplankton growth (:math:`f_{T}`).
:math:`\mathrm{N}_{dia}'` encompasses a preference term for grazing on diatoms,
relative to that on nanophytoplankton:

.. math::
   \label{eq:Ndia}
   \begin{split}
   \mathrm{N}_{dia}^{'} = \tau \cdot \frac{ \mathrm{N}_{dia}^2}{\varphi_{2} +  \mathrm{N}_{dia}^2} \cdot \mathrm{N}_{dia}
   \end{split}


Here, :math:`\tau` is the maximum diatom preference and is smaller than one,
which implies that zooplankton grazes preferably on nanophytoplankton;
the effective grazing preference is allowed to vary with diatom
biomass, with :math:`\varphi_{2}` being the half saturation parameters for 
grazing preference of diatoms. :math:`\varphi_{2}=0` implies a constant
preference.


The relative contributions of grazing on nanophytoplankton and on
diatoms to the total grazing flux are calculated by their respective
proportion to the total zooplankton food resource.  

.. math::
   \label{eq:Gphy}
   \begin{split}
   G_{phy} = G \cdot \frac{\mathrm{N}_{phy}}{ \mathrm{N}_{phy} + \mathrm{N}_{dia}^{'}} 
   \end{split}

.. math::
   \label{eq:Gdia}
   \begin{split}
   G_{dia} = G \cdot \frac{\mathrm{N}_{dia}^{'}}{ \mathrm{N}_{phy} + \mathrm{N}_{dia}^{'}} 
   \end{split}

Carbon pool (:math:`\mathrm{C}_{het}`)
--------------------------------------

The heterotrophic carbon biomass is a balance between carbon uptake
via grazing and carbon loss via mortality, carbon excretion and
respiration. 

.. math::
   \label{eq:hetC}
   \begin{split}
   S(\mathrm{C}_{het}) = &\; \left( \frac{1}{q_{phy}} \cdot  G_{phy}  + \frac{1}{q_{dia}} \cdot G_{dia} \right) \cdot \gamma - \frac{1}{q_{het}} \cdot m_{het}  \cdot \mathrm{N}_   {het}^2
   \\ 
    &\; - \epsilon^C_{het} \cdot \mathrm{C}_{het} - r_{het} \cdot \mathrm{C}_{het} 
   \end{split}

The grazing flux in terms of nitrogen biomass is converted to carbon
biomass using the respective intracellular N:C ratios
(:math:`q_{phy}` and :math:`q_{dia}`). Sloppy feeding causes some of
the grazed phytoplankton to be transferred directly to the detritus
pool, as determined by the grazing efficiency :math:`\gamma`. The remainder
is built into heterotropic biomass. The quadratic mortality flux
(:math:`m_{het}  \cdot \mathrm{N}_{het}^2`), which causes carbon to be lost to the
detritus compartment, is converted to carbon using the intracellular
heterotrophic N:C ratio (:math:`q_{het}`). 
When the C:N ratio in heterotrophs (:math:`q^{C:N}_{het}` = 1/:math:`q_{het}`)  exceeds the Redfield ratio,
heterotrophic respiration is assumed to drive the ratio back 
towards Redfield, with a time-scale :math:`\kappa_{het}`:  

.. math::
   r_{het} = \left\{ \begin{array}{lll}
   f_T \cdot (q^{C:N}_{het} - q^{C:N}_{Redfield}) / \kappa_{het} & 
   \mathrm{if} & q^{C:N}_{het} > q^{C:N}_{Redfield} \\
   0 & \mathrm{if} & q^{C:N}_{het} \le q^{C:N}_{Redfield}
   \end{array} \right.

Detritus
========
.. _sec_det:

\paragraph{Nitrogen pool (:math:`\mathrm{N}_{det}`)}
Losses of phytoplankton nitrogen due to aggregation, mortality and
sloppy feeding have to pass the :math:`\mathrm{N}_{det}` compartment before being
degraded to :math:`\mathrm{DON}`, which is the only loss term for detrital
nitrogen.

.. math::
   \label{detN}
   \begin{split}
   S(\mathrm{N}_{det}) = &\; G \cdot (1 - \gamma) + g \cdot (\mathrm{N}_{phy} + \mathrm{N}_{dia}) +
   m_{het}  \cdot \mathrm{N}_{het}^2 - \rho_{PON} \cdot f_T \cdot \mathrm{N}_{det} 
   \end{split}

See section \ref{sec:het} for a definition of the grazing flux :math:`G`,
the grazing efficiency :math:`\gamma` and the zooplankton mortality flux (:math:`m_{het} \cdot
\mathrm{N}_{het}^2`). The aggregation rate :math:`g` is defined
in Eq. \ref{eq:g}. Degradation of :math:`N_{det}` to DON is based on a constant degradation rate (:math:`\rho_{PON}`)
and a temperature dependency (:math:`f_T`, Eq. \ref{eq:arr}).

Carbon pool (:math:`\mathrm{C}_{det}`)
--------------------------------------

The :math:`\mathrm{C}_{det}` compartment is balanced by carbon sources associated
with sloppy feeding, aggregation of phytoplankton, mortality of
heterotrophs and degradation of :math:`\mathrm{C}_{det}` to :math:`\mathrm{DOC}` as the only
loss term. 

.. math::
   \label{detC}
   \begin{split}
   S(\mathrm{C}_{det}) = &\; \left( \frac{1}{q_{phy}} \cdot G_{phy}  + \frac{1}{q_{dia}} \cdot G_{dia} \right) \cdot (1-\gamma) + g \cdot (\mathrm{C}_{phy} + \mathrm{C}_{dia} ) \\ 
   &\;+ \frac{1}{q_{het} } \cdot m_{het}  \cdot \mathrm{N}_{het}^2 -\rho_{POC} \cdot f_T \cdot \mathrm{C}_{det}
   \end{split}

The grazing and the quadratic mortality flux (see section
\ref{sec:het}), which are calculated in terms of N biomass, are
converted to carbon biomass via the respective intracellular N:C
ratios (:math:`q_{phy}`, :math:`q_{dia}` and :math:`q_{het}`). The
sloppy feeding part of the grazing flux is transfered to the :math:`\mathrm{C}_{det}`
compartment, while the main grazing flux is built into heterotrophic
biomass, as determined by the grazing efficiency :math:`\gamma`. The
degradation term consists of a constant degradation rate
:math:`\rho_{POC}` and takes into account a temperature dependency :math:`f_T`
(see Eq. \ref{eq:arr}). 

Silica pool (:math:`\mathrm{Si}_{det}`)
---------------------------------------

The detrital silica budget consists of aggregation, grazing and
excretion fluxes from diatoms to detritus and silica dissolution,
which shifts silicon from :math:`\mathrm{Si}_{det}` to dissolved silicate. 

   \label{detSi}
   \begin{split}
   S(\mathrm{Si}_{det}) = &\; (g + \epsilon^N_{dia} \cdot f^{lim}_{dia}) \cdot
   \mathrm{Si}_{dia} + G_{dia} \cdot q^{Si:N}_{dia} - \rho_{Si}^T\cdot \mathrm{Si}_{det} 
   \end{split}

See section \ref{sec:phy} for definitions of the aggregation (:math:`g`) and
excretion (:math:`\epsilon`) fluxes and section \ref{sec:het} for the
grazing fluxes (:math:`G`).  

The silica dissolution rate :math:`\rho_{Si}^T` follows the temperature dependence of \citet{Kamatani1982}, until it exceeds the maximum dissolution rate 
:math:`\rho_{Si}`

.. math::
   \label{eq:sidiss}
   \rho_{Si}^T = min(1.32 \cdot 10^{16} \cdot \exp(\frac{-11200}{T}) , \rho_{Si})

\paragraph{Calcium carbonate pool (:math:`\mathrm{CaCO}_{3\,det}`)}
Nanophytoplankton loses :math:`CaCO_3` to the detrital :math:`CaCO_3` compartment
via excretion, respiration, aggregation and grazing. Dissolution of
:math:`CaCO$_3` leads to an increase in :math:`\mathrm{DIC}` and alkalinity (see section
\ref{sec:carbchem}). 

.. math::
   \label{detCaCO3}
   \begin{split}
   S(\mathrm{CaCO}_{3\,det}) = &\;  (\epsilon^C_{phy}  \cdot f^{lim}_{phy} +
   r_{phy} + g + G_{phy} \cdot q^{CaCO_3:N}_{phy}) \cdot \mathrm{CaCO}_{3\,phy} \\ 
   & \; - \lambda \cdot \mathrm{CaCO}_{3\,det}
   \end{split}

The nanophytoplankton excretion term (:math:`\epsilon^C_{phy}`) is regulated by intracellular quota as defined in
Eq. \ref{eq:f^{lim}_{phy}}. Refer to section \ref{sec:phy} for a
definition of the respiration (:math:`r_{phy}`) and the aggregation
(:math:`g`) rates. The grazing flux is calculated in terms of nitrogen biomass (Eq. \ref{eq:Gphy})
and is converted to :math:`\mathrm{CaCO}_{3\;det}` by multiplication with the
intracellular :math:`CaCO_3`:N ratio (:math:`q^{CaCO_3:N}_{phy}`).  

Detrital calcite decreases exponentially with water depth with a
vertical length scale of 3500~m according to
\citet{YamanakaTajika1996}. The dissolution rate :math:`\lambda` [:math:`d^{-1}`]
depends on the sinking speed of detritus, so that 

.. math::
   \label{eq:calcdiss}
   \lambda = \frac{w_{det}}{3500\;m} 

where :math:`w_{det}` increases with depth according to

.. math::
   \label{eq:wdet}
   w_{det} = 20 \; m\;s^{-1}+ 0.0288 \; s^{-1}\cdot \; depth (m) 



Dissolved Organic Matter (DOM)
==============================
.. _sec_dom:

Dissolved Organic Nitrogen (:math:`\mathrm{DON}`)
-------------------------------------------------

:math:`\mathrm{DON}` is produced via N excretion by nanophytoplankton, diatoms and
heterotrophs, and by degradation of detrital N. It is turned into :math:`\mathrm{DIN}` by
remineralization.

.. math::
   \label{DON}
   \begin{split}
   S(\mathrm{DON}) = &\; \epsilon^N_{phy} \cdot f^{lim}_{phy} \cdot \mathrm{N}_{phy} +
   \epsilon^N_{dia} \cdot f^{lim}_{dia} \cdot \mathrm{N}_{dia} + \epsilon^N_{het}
   \cdot \mathrm{N}_{het} \\ 
   &\;+ \rho_{PON} \cdot f_T \cdot \mathrm{N}_{det} - \rho_{\mathrm{DON}} \cdot f_T \cdot \mathrm{DON}
   \end{split}


The constant excretion rates of phytoplankton (:math:`\epsilon^N_{phy}` and
:math:`\epsilon^N_{dia}`) are reduced if the N:C ratio is larger than a
threshold (see Eq. \ref{eq:f^{lim}_{phy}} and
Eq. \ref{eq:f^{lim}_{dia}}). Heterotrophic nitrogen excretion (:math:`\epsilon^N_{het}
\cdot \mathrm{N}_{het}`) depends only on the heterotrophic biomass. Degradation
of :math:`\mathrm{N}_{det}` to :math:`\mathrm{DON}` and remineralization from :math:`\mathrm{DON}` to :math:`\mathrm{DIN}` is temperature
dependent, so that the constant degradation (:math:`\rho_{PON}`) and remineralization
(:math:`\rho_{\mathrm{DON}}`) rates are multiplied with the Arrhenius
function (:math:`f_T`, see Eq. \ref{eq:arr}).  

Dissolved Organic Carbon (:math:`\mathrm{DOC}`)
-----------------------------------------------

$\mathrm{DOC}$ sources are carbon excretion by nanophytoplankton, diatoms and
heterotrophs, and degradation of :math:`\mathrm{C}_{det}`. Remineralization of :math:`\mathrm{DOC}` leads
to a transfer of carbon from :math:`\mathrm{DOC}` to :math:`\mathrm{DIC}`.

.. math::
   \label{DOC}
   \begin{split}
   S(\mathrm{DOC}) = &\; \epsilon^C_{phy} \cdot f^{lim}_{phy} \cdot \mathrm{C}_{phy} +
   \epsilon^C_{dia} \cdot f^{lim}_{dia} \cdot \mathrm{C}_{dia} + \epsilon^C_{het}
   \cdot \mathrm{C}_{het}\\ 
   &\;+ \rho_{POC} \cdot f_T \cdot \mathrm{C}_{det}  - \rho_{\mathrm{DOC}} \cdot f_T \cdot \mathrm{DOC}
   \end{split}

Metabolic excretion of organic matter by phytoplankton is determined
by a constant excretion rate and cell quota (:math:`\epsilon^C_{phy}` and
:math:`\epsilon^C_{dia}`, see section \ref{sec:phy}). The heterotrophic
excretion rate per heterotrophic biomass is constant (:math:`\epsilon^C_{het}`). The constant
degradation (:math:`\rho_{POC}`) and remineralization (:math:`\rho_{\mathrm{DOC}}`) rates that determine
the fluxes from :math:`\mathrm{C}_{det}` to :math:`\mathrm{DOC}` and from :math:`\mathrm{DOC}` to :math:`\mathrm{DIC}` are altered
following the Arrhenius function (:math:`f_T`, Eq. \ref{eq:arr}).  


Boundary conditions and early diagenesis
========================================
.. _sec_BC:

In its present version, REcoM-2 considers neither riverine input of
nutrients, carbon and alkalinity, nor permanent burial of organic
matter, calcium carbonate and silica in the sediment. At the sea
surface, we assume no normal flux of tracers, except for :math:`\mathrm{DIC}` that
can exchange with the atmospheric reservoir of :math:`CO_2`. This surface
boundary condition can be written as

.. math::
   \label{SBC-gen}
   \left .\kappa \frac{\partial A}{\partial z}\right|_{z=\eta} = \left\{ 
   \begin{array}{lll} 
   0 & \mathrm{for} & A \ne \mathrm{DIC} \\
   F_{\mathrm{C}} & \mathrm{for} & A = \mathrm{DIC} 
   \end{array}
   \right.

where :math:`\eta` is the sea surface elevation, and the air-sea flux of
carbon :math:`F_{\mathrm{C}}` (positive for flux out of the ocean) is
calculated from :math:`\mathrm{DIC}`, :math:`\mathrm{TA}`, atmospheric :math:`pCO_2`,
temperature, salinity and wind speed, follwing OCMIP
protocols. Likewise, we assume no horizontal flux of tracers at
lateral boundaries.

At the bottom of the ocean, the sinking flux of particulates
(nanophytoplankton, diatoms and detritus) is directed into a
homogeneous sediment layer, where POC and PON are degraded and instantaneously remineralized and calcium
carbonate and silica are dissolved with fixed rates. The corresponding
equations are 

.. math::
   \begin{split}
   \frac{\partial \mathrm{POC}_{sed}}{\partial t} = &\; w_{det} \cdot \mathrm{C}_{det}
   - d^C \cdot \mathrm{POC}_{sed} \\ 
   \frac{\partial \mathrm{PON}_{sed}}{\partial t} = &\; w_{det} \cdot \mathrm{N}_{det}
   - d^N \cdot \mathrm{PON}_{sed} \\ 
   \frac{\partial \mathrm{Si}_{sed}}{\partial t} = 
   &\; w_{det}\cdot  \mathrm{Si}_{det} - d^{Si}
   \cdot \mathrm{Si}_{sed} \\ 
   \frac{\partial \mathrm{CaCO}_{3\,sed}}{\partial t} = 
   &\; w_{det} \cdot
   \mathrm{CaCO}_{3\,det} - d^{CaCO_3} \cdot \mathrm{CaCO}_{3\,sed}
   \end{split}

where :math:`\mathrm{POC}_{sed}`, :math:`\mathrm{POC}_{sed}`, :math:`\mathrm{Si}_{sed}`,
and :math:`\mathrm{CaCO}_{3\,sed}` are vertically integrated 
concentrations in the sediment layer, i.e.\ they have the unit mol :math:`m^{-2}`. :math:`d^{C}`, :math:`d^{N}`, :math:`d^{Si}`, and :math:`d^{CaCO_3}` 
are the degradation or dissolution rates for POC, PON, Si and :math:`CaCO_3`, respectively.

The nutrients and alkalinity released during the degradation/remineralization and
dissolution are directly returned into the water as a
flux, i.e.\ the boundary condition at the ocean bottom is

.. math::
   \label{SBC-gen-a}
   \left .\kappa \frac{\partial A}{\partial z}\right|_{z=-H} = \left\{ 
   \begin{array}{lll} 
   d^C \cdot \mathrm{POC}_{sed} + d^{CaCO_3} \cdot \mathrm{CaCO}_{3\,sed} & \mathrm{for} & A = \mathrm{DIC} \\ 
   d^N \cdot \mathrm{PON}_{sed} & \mathrm{for} & A = \mathrm{DIN} \\ 
   (1+1/16) \cdot d^N \cdot \mathrm{PON}_{sed} + 2d^{CaCO_3} \cdot \mathrm{CaCO}_{3\,sed} & \mathrm{for} & A = \mathrm{TA} \\ 
   d^{Si} \cdot \mathrm{Si}_{sed} & \mathrm{for} & A = \mathrm{DSi} \\ 
   q^{Fe} \cdot d^C \cdot \mathrm{POC}_{sed} & \mathrm{for} & A = \mathrm{DFe} \\ 
   0 & \mathrm{for} & \mbox{all other tracers}
   \end{array}
   \right.

Tables
======
.. _sec_table:

.. table:: Model coefficients and their standard values
   :widths: 10 20 30 50

   +----------------------------------+-----------+------------------+-------------------------+
   | Symbol                           | Value     | Unit             | Parameter               |
   +==================================+===========+==================+=========================+
   | :math:`T_{ref}`                  | 288.15    | K                | reference temperature   |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\psi`                     | 0.02      | dimensionless    | calcite                 |
   |                                  |           |                  | production ratio        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q^{Fe}`                   | 0.005     | :math:`\mu`      | Fe:C ratio              |
   |                                  |           | mol\ Fe (mmol C) |                         |
   |                                  |           | :math:`^{-1}`    |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\kappa^{scav}_{Fe}`       | 0.0156    | (mmol\ C\ m      | Fe scavenging           |
   |                                  |           | :math:`^{-3}`)   | rate                    |
   |                                  |           | :math:`^{-1}`d   |                         |
   |                                  |           | :math:`^{-1}`    |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\alpha_{phy}`             | 0.14      | mmol C (mg Chl)  | initial slope of        |
   |                                  |           | :math:`^{-1}`    | P-I curve               |
   |                                  |           | (Wm              |                         |
   |                                  |           | :math:`^{-2}`    |                         |
   |                                  |           | d :math:`^{-1}`) |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\alpha_{dia}`             | 0.19      | mmol C (mg Chl)  | diatom initial          |
   |                                  |           | :math:`^{-1}`    | slope of P-I            |
   |                                  |           | (Wm              | curve                   |
   |                                  |           | :math:`^{-2}`    |                         |
   |                                  |           | d :math:`^{-1}`) |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\mu^{max}_{phy}`          | 3.0       | d\ :math:`^{-1}` | maximum                 |
   |                                  |           |                  | photosynthesis rate     |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\mu^{max}_{dia}`          | 3.5       | d\ :math:`^{-1}` | diatom maximum          |
   |                                  |           |                  | photosynthesis rate     |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\epsilon^N_{phy}`         | 0.05      | d\ :math:`^{-1}` | excretion rate          |
   |                                  |           |                  | of nitrogen             |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\epsilon^N_{dia}`         | 0.05      | d\ :math:`^{-1}` | diatom excretion        |
   |                                  |           |                  | rate of nitrogen        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\epsilon^C_{phy}`         | 0.10      | d\ :math:`^{-1}` | excretion rate of carbon|
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\epsilon^C_{dia}`         | 0.10      | d\ :math:`^{-1}` | diatom excretion        |
   |                                  |           |                  | rate of carbon          |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\sigma_{phy}^N`           | 0.20      | mol N (mol C)    | N:C uptake ratio        |
   |                                  |           | \ :math:`^{-1}`  |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\sigma_{dia}^N`           | 0.20      | mol N (mol C)    | diatom N:C              |
   |                                  |           | \ :math:`^{-1}`  | uptake ratio            |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\sigma_{dia}^{Si}`        | 0.20      | mol Si (mol C)   | diatom Si:C             |
   |                                  |           | \ :math:`^{-1}`  | uptake ratio            |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`K_{phy}^{\mathrm{N}}`     | 0.55      | mmol N           | half-saturation         |
   |                                  |           | m\ :math:`^{-3}` | constant N uptake       |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`K_{dia}^{\mathrm{N}}`     | 1.0       | mmol N           | diatom half-saturation  |
   |                                  |           | m\ :math:`^{-3}` | constant N uptake       |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`K^{Fe}_{phy}`             | 0.02      | :math:`\mu`\molFe| half-saturation         |
   |                                  |           | m\ :math:`^{-3}` | constant Fe uptake      |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`K^{Fe}_{dia}`             | 0.12      | :math:`\mu`\molFe| diatom half-saturation  |
   |                                  |           | m\ :math:`^{-3}` | constant Fe uptake      |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`K_{dia}^{\mathrm{Si}}`    | 4.0       | mmol Si          | diatom half-saturation  |
   |                                  |           | m\ :math:`^{-3}` | constant Si uptake      |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{phy\,max}`             | 0.20      | mol N (mol C)    | maximum N:C ratio       |
   |                                  |           | \ :math:`^{-1}`  |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{dia\,max}`             | 0.20      | mol N (mol C)    | diatom maximum          |
   |                                  |           | \ :math:`^{-1}`  |  N:C ratio              |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{max}^{Si}`             | 0.80      | mol Si (mol C)   | diatom maximum          |
   |                                  |           | \ :math:`^{-1}`  | Si:C ratio              |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{min}`                  | 0.04      | mol N (mol C)    | minimum N:C ratio       |
   |                                  |           | \ :math:`^{-1}`  |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{min}^{Si}`             | 0.04      | mol Si (mol C)   | minimum Si:C ratio      |
   |                                  |           | \ :math:`^{-1}`  |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{phy\,max}^{Chl:N}`     | 3.15      | mg Chl (mmol N)  | nanophytoplankton       |
   |                                  |           | \ :math:`^{-1}`  | maximum Chl:N  ratio    |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`q_{dia\,max}^{Chl:N}`     | 4.2       | mg Chl (mmol N)  | diatom maximum          |
   |                                  |           | \ :math:`^{-1}`  | Chl:N ratio             |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\theta_{max}`             | 1000      | dimensionless    | regulation slope        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\theta_{min}`             | 50        | dimensionless    | regulation slope        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\theta_{min}^{Si}`        | 1000      | dimensionless    | regulation slope        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\theta_{max}^{Si}`        | 1000      | dimensionless    | regulation slope        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\zeta^{N}`                | 2.33      | mol C (mol N)    | C cost of N             |
   |                                  |           | \ :math:`^{-1}`  | assimilation            |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\zeta^{Si}`               | 0         | mol C (mol Si)   | C cost of Si            |
   |                                  |           | \ :math:`^{-1}`  | assimilation            |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\phi_{phy}`               | 0.015     | (mmol N m        | phytoplankton           |
   |                                  |           | \ :math:`^{-3}`) | specific                |
   |                                  |           | \ :math:`^{-1}`d | aggregation rate        |
   |                                  |           | \ :math:`^{-1}`  |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\phi_{det}`               | 0.165     | (mmol N m        | detrius specific        |
   |                                  |           | \ :math:`^{-3}`) | aggregation rate        |
   |                                  |           | \ :math:`^{-1}`d |                         |
   |                                  |           | \ :math:`^{-1}`  |                         |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\eta_{phy}`               | 0.01      | d\ :math:`^{-1}` | maintenance             |
   |                                  |           |                  | respiration rate        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\eta_{dia}`               | 0.01      | d\ :math:`^{-1}` | diatom maintenance      |
   |                                  |           |                  | respiration rate        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`d^{Chl}_{phy}`            | 0.3       | d\ :math:`^{-1}` | chlorophyll             |
   |                                  |           |                  | degradation rate        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`d^{Chl}_{dia}`            | 0.3       | d\ :math:`^{-1}` | diatom chlorophyll      |
   |                                  |           |                  | degradation rate        |
   +----------------------------------+-----------+------------------+-------------------------+
   | :math:`\gamma`                   | 0.4       | dimensionless    | grazing                 |
   |                                  |           |                  | efficiency              |
   +----------------------------------+-----------+------------------+-------------------------+
