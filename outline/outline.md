# Analysing Directional Data using VectoRose

Benjamin Z. Rudski

## Brief Outline

This outline presents a broad overview of the topics to be covered in the
bootcamp. See below for a more detailed outline of the material covered.

1. Theory (1 hour)
    1. Introduction to directed data
    2. Data Visualisation
    3. Introduction to directional statistics
    4. Combining magnitudes and directions/orientations
2. Hands-on examples (2 hours)
    1. Introduction to VectoRose
    2. Extracting microtubule orientations
    3. Understanding trabecular anisotropy
3. Summary (5 minutes)

## Detailed Outline

This section provides more detailed insight into the material that will be
discussed during the VectoRose bootcamp.

1. **Theory (1 hour)**  
    This section aims to provide participants with a basic introduction to
    the problem at hand.

    1. **Introduction to directed data**  
    This section introduces the basic notions of vectorial and axial data.
    Examples will be provided to help participants understand why classical
    statistical and visualisation approaches are insufficient for these
    types of data. This section will serve to motivate and provided a basis
    for all the content that follows.  
        * **Problem setting**: provide different examples of data that don't
        follow a nice Euclidean grid (e.g., time of day, wind speed, 3D
        structural orientations).
        * **Vectorial and axial data**: introduce the two types of oriented
        data that can exist, and provide analogies and explanations to clarify
        the difference between these two. Explain the angular representation
        for each (define $\phi$ and $\theta$, making it clear that there are
        **many** different ways of defining these angles).
        * **Motivational questions**: leave the audience with some questions
        that will motivate this bootcamp. For example: How can we visualise a
        collection of different orientations to get a visual summary? How can
        we find an average orientation? How can we talk about how the
        orientations are clustered together? How do we describe patterns on
        the surface of the sphere? We'll start seeing how we can do all this.
    2. **Data visualisation**  
    This section introduces the basic ideas of data visualisation that will
    help provide useful insight to directed data.
        * **Types of plots**: introduce the types of plots that can be
        constructed, specifically scatter plots and histograms.
        * **Discretising the sphere**: a sphere is a perfect 3D object. This
        presents a number of issues. This section covers how the sphere can
        be represented in 2D, and how it can be divided to ensure that all
        faces have similar areas.
    3. **Directional statistics**  
    This section provides a basic introduction to some directional statistics
    operations that can be performed to gain new insight into the data under
    consideration.
        * **Descriptive statistics**: present simple metrics that can be used
        to describe directional distributions. In this section, we will start
        off with the *resultant vector* and the *mean resultant length*,
        which offer a summary of the overall orientation of the data and a
        simple, albeit flawed, measurement of how dispered the data are. Then,
        we will also cover the spherical median direction. We will next cover
        the *moment of inertia* analysis using the *orientation matrix*. This
        matrix helps define an ellipsoid that represents the distributions of
        directions or orientations in 3D. The eigenvalues of this matrix can
        also be used to compute Woodcock's shape and strength parameters, which
        can be used to describe the overall shape of the distribution (uniform
        vs. cluster vs. girdle).
        * **Von Mises-Fisher distribution**: this section will briefly
        introduce the concept of the von Mises-Fisher distribution, the
        directional equivalent of the normal distribution. We won't get very
        far into the math of this distribution. Instead, the discussion will
        be very high-level, focussing on the two parameters that define this
        distribution: the mean direction $\mu$ and the concentration parameter
        $\kappa$. We'll discuss how these affect the distribution, and we'll
        see that it is possible to estimate these parameters based on data.
    4. **Combining magnitudes and directions/orientations**  
    This section takes things a step farther. Everything up until now has
    focused on pure directions or orientations, which consist of unit vectors
    or unit axes. But, some quantities have both direction and magnitude.
    In this section, we will briefly discuss how these different quantities
    can be related to each other.
        * **Analysing and representing non-unit vectors**: We have statistics
        for dealing with scalar quantities and we have statistics for dealing
        with unit vectors, but we don't have many tools for dealing with
        non-unit vectors. Here, we will present a way of looking at non-unit
        vectors as a *bivariate distribution*, consisting of two separate but
        linked variables corresponding to the direction/orientation and the
        magnitude. We'll discuss important ideas such as *joint*, *marginal*
        and *conditional* distributions. We'll also discuss what these each
        mean in terms of the analyses we can perform, both visually and
        statistically.

2. **Hands-on (2 hours)**
    After having covered the necessary theory in the previous section, this
    section provides participants with the opportunity to apply the material
    using VectoRose, a new Python package. First, we'll see the basics of
    VectoRose, and then we'll apply it to some real-world biological data to
    illustrate the key concepts described above.

    > **Note:** This section will consist of live-coding exercises using a
    > Jupyter notebook. Solutions will be provided as well in advance for
    > students who want to follow along without worrying about typing
    > everything in real-time.

    1. **Introduction to VectoRose**  
    This section provides an introduction to the tool that we'll use to analyse
    the directional data.
        * **About VectoRose**: Talk briefly about VectoRose, that it is built
        on existing, established Python packages, like NumPy, pandas, PyVista.
        Also show the online documentation.
        * **Installing VectoRose**: Show how to install VectoRose using `pip`
        (I will likely prepare an installation guide before the workshop to
        ensure that everybody has all necessary packages installed).
        * **Setting up VectoRose**: Open Jupyter Lab and navigate to the files
        for the bootcamp.
    2. **Extracting microtubule orientations**  
    This section provides a first hands-on example showing how to apply
    VectoRose to real data. The data used here are cryotomography images of
    microtubules, generously provided by Dr. Bui. This section will consist
    of a worked example showing a standard analysis pipeline using VectoRose.
        * **Loading and preprocessing data**: open vectors from a file and
        clean the dataset by removing zero-vectors and (in the case of axial
        data) flipping all vectors to the upper hemisphere. Perhaps the vectors
        will also be visualised in 3D.
        * **Computing an orientation histogram**: create a representation of a
        sphere and assign all vectors to an orientation bin. Then, collect all
        the bins to create a histogram based on count or frequency.
        * **Visualising an orientation histogram**: view the spherical
        histogram in 3D in the Jupyter notebook using PyVista.
        * **Creating sphere animations (optional)**: export an animation of the
        spherical histogram rotating about its axis.
        * **Directional statistics**: Compute directional statistics, including
        the resultant vector and the mean resultant length, Woodcock's shape
        and strength parameters, and, if appropriate, the von Mises-Fisher
        parameters.
        * **Exercise:** Repeat this process with a new, similar dataset.
        * **Note:** Supplemental information may be provided explaining how
        these vectors were computed (for anybody interested).
    3. **Understanding trabecular anisotropy**  
    This section provides a worked example centered on a case where both the
    orientation and the magnitude are important. We will construct a series of
    nested spherical histograms that can be viewed interactively. We will also
    compute directional statistics on both the marginal and conditional
    distributions to gain insight into the bone architecture. These analyses
    will also reveal the importance of considering magnitude when analysing
    orientation.
        * **Loading and preprocessing data**: Similar to above.
        * **Computing a joint histogram of magnitude and oreintation**: create
        a representation of a sphere with several nested magnitude bins. Assign
        each vector to both magnitude and orientation bins. Collect all bin
        assignments to create the joint histogram using counts and/or
        frequencies.
        * **Visualising a joint histogram**: view the joint histogram using a
        series of nested spheres in 3D. See how to use the interactive sliders
        to control the visibility of the various shells.
        * **Creating nested sphere animations (optional)**: export an animation
        iterating through all the spheres to show the distributions at different
        magnitude levels.
        * **Directional statistics**: compute directional statistics of both
        the marginal orientation distribution and the conditional distributions
        at specific spherical shells. In each case, Woodcock's parameters will
        be computed, among other metrics.
        * **Exercises**:
            1. Repeat the analysis with a new, similar dataset.
            2. Using the provided links to the documentation, construct the
            marginal histograms of orientation and magnitude separately.
        * **Note:** Supplemental information may be provided detailing how the
        vectors were computed.
3. **Summary**  
This section will conclude the bootcamp. We will quickly summarise the material
that was covered, and we will see how to learn more above VectoRose. There will
also be an acknowledgements slide thanking everyone involved in developing and
releasing VectoRose, as well as the CRBS for the opportunity to lead this
bootcamp and for all their support in this endeavor.
