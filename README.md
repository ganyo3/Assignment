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
            The Hamiltonian Matrix is also given as : <h4>H[i,j] = 2/$dx^2$ + V[i]</h4> where dx is the spacing between the points, and V[i] is the potential energy at the i-th point.
 We will use the numpy.linalg.eigh() function to solve the eigenvalue problem and obtain the energy eigenvalues and wavefunctions. '
 We will then plot the energy eigenvalues and wavefunctions as a function of "a" and "V" using the matplotlib library.'
         
   
import numpy as np
import matplotlib.pyplot as plt
class ParticleInABox:
    def __init__(self, a, b, V, N=1000):
        self.a = a
        self.b = b
        self.V = V
        self.N = N
        self.dx = (b-a)/N
        self.x = np.linspace(a, b, N)
        self.psi = np.zeros(N)
        self.Vx = np.zeros(N)
        self.H = np.zeros((N, N))

    def set_potential(self):
        for i in range(self.N):
            if self.a <= self.x[i] <= self.b:
                self.Vx[i] = self.V
            else:
                self.Vx[i] = np.inf

    def set_hamiltonian(self):
        self.H = np.zeros((self.N, self.N))
        for i in range(1, self.N-1):
            self.H[i,i] = -2/self.dx**2 + self.Vx[i]
            self.H[i,i+1] = 1/self.dx**2
            self.H[i,i-1] = 1/self.dx**2

        # Boundary conditions
        self.H[0,0] = 1
        self.H[0,1] = 0
        self.H[-1,-1] = 1
        self.H[-1,-2] = 0

    def solve(self):
        self.set_potential()
        self.set_hamiltonian()
        self.energy, self.wavefunction = np.linalg.eigh(self.H)
        self.psi = self.wavefunction[:,0]

    def plot_wavefunction(self):
        plt.plot(self.x, self.psi)
        plt.title("Wavefunction")
        plt.xlabel("x")
        plt.ylabel("psi(x)")
        plt.show()

    def plot_energy(self):
        plt.plot(self.energy)
        plt.title("Energy Eigenvalues")
        plt.xlabel("n")
        plt.ylabel("Energy")
        plt.show()

if __name__ == "__main__":
    a = 0
    b = 1
    V = 1
    pib = ParticleInABox(a, b, V)
    pib.solve()
    pib.plot_wavefunction()
    pib.plot_energy()
                
            
