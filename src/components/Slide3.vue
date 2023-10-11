<template>
    <div class="card">
        <div class="card__title">
            <h2>Integration of Wind Farms into Electrcity Grids</h2>
            <h3>Workshop by Vestas</h3>
        </div>
        <div class="card__description">
            <p>This workshop will cover the representation of wind farms in simulation software, with an emphasis on wind
                turbine design and electrical performance for compliance with grid requirements.</p>
        </div>
    </div>
</template>

<style scoped>
.card {
    color: #1a1a1a;
    display: flex;
    flex-direction: column;
    font-family: Kanit, sans-serif;
    justify-content: space-between;
    overflow-x: hidden;
    overflow-y: auto;
    padding: 30px 60px;
    text-align: left;
}

.card__title {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.card__title h2 {
    font-size: 3rem;
    font-weight: 600;
    line-height: 3.4rem;
}

.card__title h3 {
    font-size: 2rem;
    font-weight: 700;
    padding-top: 0.2rem;
    width: 50%;
}

.card__description {
    padding-top: 1rem;
}

.card__description p {
    font-size: 1.6rem;
    text-align: left;
}
</style>