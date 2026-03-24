## Additional Information

**Have I participated in GSoC before?**
No, this is my first time applying to GSoC. However, I have extensive experience with intensive coding projects through hackathons and open source contributions.

**Why this specific project (Testing Suite)?**
I chose the Automated Testing Suite project because it directly matches my demonstrated skills. I've already submitted PR #607 with 61 pytest tests, proving I can deliver exactly what this project requires. Testing infrastructure is foundational work that will benefit all future gprMax development.

**What I hope to learn:**
- Deep understanding of FDTD electromagnetic simulation theory
- Physics validation testing methodologies
- Cross-platform CI/CD best practices for scientific software
- How to design test suites that balance coverage with execution speed

**Expectations from mentors:**
- Weekly guidance on project priorities and technical direction
- Code review feedback on PRs
- Help understanding gprMax physics concepts when needed for validation tests
- Access to existing benchmark data for physics validation

**Experience with C and CUDA:**
My experience is primarily in Python. I have basic familiarity with C syntax from systems programming coursework, but this project focuses on Python-based pytest testing and does not require C or CUDA development.

**Assumptions:**
1. The existing integration tests in `tests/models_basic/` will remain the ground truth for physics correctness
2. New unit tests should be fast (<1 second each) to enable rapid CI feedback
3. Physics validation tests may be slower but will run in a separate CI job
4. Mock imports can be used to test modules in isolation without full gprMax installation

**Project Management:**
I will use GitHub Projects for task tracking with weekly sprints. Each week I'll create issues for planned tasks, link PRs to issues, and update progress. This provides mentors visibility without requiring separate tools.

**Communication Plan:**
- **Weekly sync:** 30-minute video call (flexible timing for UK/Taiwan zones)
- **Daily async:** Progress updates on Zulip or GitHub
- **All code:** Through GitHub PRs for transparent review
- **Blockers:** Raise immediately via Zulip, don't wait for weekly sync

**Community Bonding Goals (May 26 - Jun 1):**
1. Set up complete development environment on Windows
2. Run all existing tests and understand current test structure
3. Study gprMax documentation, especially physics theory
4. Review `tests/models_basic/` to understand validation patterns
5. Create detailed sprint plan with mentor input
6. Identify any dependencies or blockers early

**Most Difficult Aspect:**
Physics validation tests. Creating tests that verify numerical accuracy against analytical solutions (e.g., Hertzian dipole radiation patterns) requires deep understanding of electromagnetic theory. I plan to address this by:
- Studying existing benchmark models in detail
- Reading gprMax documentation on FDTD theory
- Asking mentors for guidance on validation methodologies
- Starting with simpler validations before complex ones

**Easiest Aspect:**
pytest infrastructure setup and utility function testing. I've already demonstrated this with PR #607 (61 tests for utilities.py). Extending this pattern to other modules like constants.py and exceptions.py is straightforward.

**Skype/Discord for contact:**
Discord: @ellatso (preferred)