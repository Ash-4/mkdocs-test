When you have turnouts that face each other, its awkward for the throttle user to have to manually switch 
both to match each other. By treating the crossover as a single turnout, control is simplified and incorrect combinations are prevented.

To do this, we need to hide one of the turnouts from the user, and make sure that throwing/closing the visible turnout automatically throws/closes the other turnout.

All turnout definitions in EXRAIL allow for a text description to be shown to the user throttle. The HIDDEN keyword, used instead of a turnout description prevents it being visible to the throttle or JMRI/iTrain etc.
 
<exrail>
TURNOUTL(1,101,"Cross inner to outer")
TURNOUTL(2,102,HIDDEN)

ONTHROW(1) THROW(2) DONE
ONCLOSE(1) CLOSE(2) DONE
</exrail>
 