document.querySelectorAll(".course button").forEach(button => {
    button.addEventListener("click", () => {
        const courseDiv = button.parentElement;
        button.disabled = true;
        button.innerText = "✓ Aprobado";
        courseDiv.classList.add("approved");

        // Revisa si desbloquea algún curso
        document.querySelectorAll(".course").forEach(otherCourse => {
            const prereq = otherCourse.getAttribute("data-prereq");
            if (prereq && prereq === courseDiv.id) {
                const otherButton = otherCourse.querySelector("button");
                otherButton.disabled = false;
            }
        });
    });
});
