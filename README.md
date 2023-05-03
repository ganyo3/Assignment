# Assignment
Numerically Solving the Time Independent Schrödinger Equation
'<h1>COMPUTATIONAL PHYSICS</h1>'
             '<p>Computational Physics is the field that combines physics and computer science to solve complex physical problems using numerical methods</p>'
             'It involves the development and implementation of algorithms, computational models, and simulations to study and analyze physical phenomena that cannot be easily solved analytically,such as the Schrödinger Equation.'
             '<p>The Schrödinger equation describes the behavior of quantum mechanical systems, and its solutions give the wave function of the system, which describes the probability of finding the particle at a particular location and time</p>'
             '<h2>OBJECTIVE</h2>'
            'The objective of this study is to use computational physics to investigate the effect of the well width a and the barrier height V on the energy eigenvalues and wavefunctions of the particle,using the'
            ' finite difference method to discretize the wavefunction and potential energy function and solve the resulting eigenvalue problem using the numpy library, then plot the energy eigenvalues and '
            'wavefunctions as a function of a and V using the matplotlib library and discuss the physical significance of the results.'
            '<h2>METHODS AND RESULTS</h2>'
             '<p>To solve the time-independent Schrödinger equation for a particle in a one-dimensional potential well, we will use the finite difference method to discretize the wavefunction and potential energy function.</p>'
            'Calculate the wavefunction and the potential energy at each point using the given potential energy function. Using the numpy library, solve the eigenvalue problem which is given by : <h4>[H][psi] = E[psi]</h4>'
            'where [H] is the Hamiltonian matrix, [psi] is the wavefunction vector, and E is the energy eigenvalue. '
            '<p>The Hamiltonian Matrix is also given as : <h4>H[i,j] = 2/$dx^2$ + V[i]</h4> where dx is the spacing between the points, and V[i] is the potential energy at the i-th point.</p>'
            'We will use the numpy.linalg.eigh() function to solve the eigenvalue problem and obtain the energy eigenvalues and wavefunctions. '
            'We will then plot the energy eigenvalues and wavefunctions as a function of "a" and "V" using the matplotlib library.\n\n'
            
