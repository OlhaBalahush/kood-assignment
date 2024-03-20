<script>
    // simple example of possible data
    let skills = [
        {
            skill: "mobile development",
            doneProjects: 4,
            allProjects: 20,
            firstProject: "mobile-app-1",
        },
        {
            skill: "web development",
            doneProjects: 20,
            allProjects: 25,
            firstProject: "web-app-1",
        },
        {
            skill: "data analysis",
            doneProjects: 10,
            allProjects: 18,
            firstProject: "data-analysis-1",
        },
        {
            skill: "machine learning",
            doneProjects: 9,
            allProjects: 30,
            firstProject: "ml-project-1",
        },
        {
            skill: "cloud computing",
            doneProjects: 3,
            allProjects: 15,
            firstProject: "cloud-project-1",
        },
        {
            skill: "cybersecurity",
            doneProjects: 8,
            allProjects: 22,
            firstProject: "security-project-1",
        },
        {
            skill: "Go",
            doneProjects: 16,
            allProjects: 20,
            firstProject: "ml-project-1",
        },
        {
            skill: "JS",
            doneProjects: 20,
            allProjects: 25,
            firstProject: "cloud-project-1",
        },
        {
            skill: "HTML",
            doneProjects: 28,
            allProjects: 30,
            firstProject: "security-project-1",
        },
        {
            skill: "Elementary algorithms",
            doneProjects: 9,
            allProjects: 20,
            firstProject: "ml-project-1",
        },
        {
            skill: "Elementary programming",
            doneProjects: 15,
            allProjects: 15,
            firstProject: "cloud-project-1",
        },
    ];

    let upcomingSkills = [
        {
            skill: "networking",
            doneProjects: 0,
            allProjects: 10,
            firstProject: "networking-project-1",
        },
        {
            skill: "game development",
            doneProjects: 0,
            allProjects: 20,
            firstProject: "game-dev-1",
        },
        {
            skill: "devops",
            doneProjects: 0,
            allProjects: 15,
            firstProject: "devops-project-1",
        },
        {
            skill: "blockchain",
            doneProjects: 0,
            allProjects: 25,
            firstProject: "frameworks-project-1",
        },
        {
            skill: "Docker",
            doneProjects: 0,
            allProjects: 8,
            firstProject: "docker-project-1",
        },
        {
            skill: "Django",
            doneProjects: 0,
            allProjects: 15,
            firstProject: "django-project-1",
        },
    ];
</script>

<div class="done-skills-cont">
    {#each skills as skill}
        <div class="skill-cont">
            <div class="fr sb">
                <div class="upper-t">{skill.skill}</div>
                <div class="add-t">
                    {skill.doneProjects} / {skill.allProjects}
                    projects
                </div>
            </div>
            <div class="gray-line">
                <div
                    class="p-line"
                    style="width: calc({(skill.doneProjects /
                        skill.allProjects) *
                        100}%);"
                >
                    <span>
                        {(
                            (skill.doneProjects / skill.allProjects) *
                            100
                        ).toFixed(0)}%
                    </span>
                </div>
            </div>
        </div>
    {/each}
</div>
<div class="up-skills">Upcoming Skills</div>
<div>
    {#each upcomingSkills as skill}
        <div class="fr g1 up-skill-cont">
            <div class="line">
                <div class="bullet-point"></div>
            </div>
            <div class="fr sb up-skill">
                <div class="upper-t m">{skill.skill}</div>
                <div class="add-t m">
                    {skill.allProjects} projects |
                    <!-- svelte-ignore a11y-invalid-attribute -->
                    <a class="skill-a" href="#">{skill.firstProject}</a>
                </div>
            </div>
        </div>
    {/each}
</div>

<style>
    .line {
        height: 100%;
        width: 2px;
        background-color: var(--gray-1);

        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }

    .bullet-point {
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background-color: var(--gray-1);
    }

    .up-skills {
        border-bottom: 1px solid var(--gray-1);
        padding-bottom: 0.25rem;
    }

    .skill-cont {
        display: flex;
        flex-direction: column;
        gap: 0.375rem;
    }

    .done-skills-cont {
        display: flex;
        flex-direction: column;
        gap: 0.75rem;
    }

    .up-skill-cont {
        height: 35px;
        width: 100%;
        min-width: 300px;
    }

    .up-skill {
        height: 35px;
        width: 100%;
    }

    .skill-a {
        text-decoration: underline;
    }

    .gray-line {
        background-color: var(--bg-color-1);
        height: 1rem;
        border-radius: 0.5rem;
    }

    .p-line {
        height: 100%;
        background-color: var(--accent-2);
        text-align: right;
        border-radius: 0.5rem;
        font-size: var(--add-text-font-size);
    }

    .p-line span {
        padding-right: 0.5rem;
        color: var(--text-light);
    }

    @media (max-width: 1400px) {
        .up-skill-cont {
            height: 50px;
        }

        .up-skill {
            flex-direction: column;
            height: auto;
            justify-content: flex-start;
        }
    }
</style>