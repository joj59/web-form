<template>
    <form>
        <label>email</label>
        <input type="email" required v-model="email" />
        <label>password</label>
        <input type="email" required v-model="password" />

        <label>role</label>
        <select v-model="role">
            <option value="developer">web developer</option>
            <option value="designer">web designer</option>
        </select>

        <label>Skills</label>
        <input type="text" required v-model="tempSkill" @keyup.alt="addSkill" />
        <div v-for="skill in skills" :key="skill" class="pill" @click="removeSkill">{{ skill }}</div>

        <div class="terms">
            <input type="checkbox" v-model="checkbox" />
            <label>terms and conditions</label>
        </div>
    </form>

    <p>email: {{ email }}</p>
    <p>password:{{ password }}</p>
    <p>role:{{ role }}</p>
    <p>checkbox:{{ checkbox }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: '',
            checkbox: false,
            tempSkill: '',
            skills: [],
        };
    },
    methods: {
        addSkill(e) {
            if (e.key === ',' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill);
                }

                this.tempSkill = '';
            }
        },
        removeSkill(e) {
            let test = this.skills.findIndex(() => e.target.innerText);
            this.skills.splice(test, 1);
        },
    },
};
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input,
select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type='checkbox'] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
</style>
