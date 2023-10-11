<template>
    <div id="wrapper">
        <h2 id="date"> <span>{{ month }}</span>&nbsp<span>{{ day }}</span><span class="fill"></span> </h2>
        <h2 id="time"> <span class="fill"></span><span> {{ hour }}</span>:<span> {{ minute }}</span>:<span>{{ seconds
        }}</span> </h2>
    </div>
</template>

<script>
export default ({
    data() {
        return {
            month: "Jan",
            day: "1st",
            hour: "00",
            minute: "00",
            seconds: "00"
        }
    },
    mounted() {
        this.currentDate();
    },
    methods: {
        currentDate() {
            setTimeout(() => {
                const date = new Date();

                // const monthNames = ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"];
                const monthNames = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];

                this.month = monthNames[date.getMonth()];
                switch (date.getDate()) {
                    case 1:
                        this.day = date.getDate() + "st";
                        break;
                    case 2:
                        this.day = date.getDate() + "nd";
                        break;
                    case 3:
                        this.day = date.getDate() + "rd";
                        break;
                    default:
                        this.day = date.getDate() + "th";
                        break;
                }
                this.hour = date.getHours();
                if (date.getMinutes() < 10) {
                    this.minute = "0" + date.getMinutes();
                } else { this.minute = date.getMinutes(); }
                if (date.getSeconds() < 10) {
                    this.seconds = "0" + date.getSeconds();
                } else { this.seconds = date.getSeconds(); }

                this.currentDate();
            }, 1000);
        }
    }
});
</script>

<style scoped>
#wrapper {
    color: white;
    display: flex;
    flex-direction: column;
    font-family: "Source Code Pro", monospace;
    font-size: 1.3rem;
    font-weight: 700;
    justify-content: center;
    align-items: flex-end;
    width: 100px;
    min-width: 200px;
}

#wrapper h2 {
    display: flex;
    flex-wrap: wrap;
}
</style>